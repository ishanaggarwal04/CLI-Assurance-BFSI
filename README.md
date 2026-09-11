# Kane CLI Assurance Pipeline for GitHub Actions

A reusable pipeline that runs `kane-cli` browser tests (`*_test.md`) in GitHub Actions. It
shards them across runners and publishes sealed **evidence packs**, per-test results and a
browsable run history. Test credentials come from **GitHub secrets** through `{{placeholders}}`,
so they're never committed.

Use this repo as a reference. Copy the workflow, point it at your own website, add your
credentials as secrets, and commit your tests.

The example wired in here tests `https://qaplayground.com/bank/login`, a demo app whose test
credentials are printed on its own login page. That's the only reason this repo keeps them in a
committed seed file. [Credentials and test data](#credentials-and-test-data) shows how to set up
an app whose credentials are private.

---

## How it works

```
your requirements doc (.md)
        │  kane-cli context ingest + design tests      ── on your machine
        ▼
.testmuai/tests/*_test.md   (steps use {{placeholders}} for credentials and URLs)
        │  git push                                    ── GitHub Actions from here
        ▼
select-tests   which tests to run (changed / all / a list)
        ▼
run-tests      N runners × M workers
               seed file + KANE_VAR_* secrets/variables → runtime variables → preflight → kane-cli testrun
        ▼
aggregate      pass/fail counts + Result.md per test in the job summary · all-results artifact
publish-results  test-results branch: latest/ + last 30 runs
```

Tests are designed locally, where you can answer the agent's questions and review what it
produces. CI only runs the committed tests. It never designs or rewrites them.

## What's in the repo

| Path | What it is | When adopting |
|---|---|---|
| `.github/workflows/kane-assurance.yml` | The pipeline | **Copy as-is** |
| `.gitignore` (the `.testmuai/...` lines) | Keeps run output and runtime variables out of git | **Copy these lines** |
| `kane-variables.seed.json` | Non-secret values for `{{placeholders}}` | **Replace** with your own non-secret values, or delete it |
| `.testmuai/tests/*_test.md` | The tests CI runs | **Replace** with tests designed for your app |
| `.context/` | The assurance graph: requirements → use-cases → acceptance criteria → tests. Committed so the test lineage is reviewable. | **Regenerated** when you design your own tests |
| `bank-demo-prd.md`, `*.pdf` | The example's requirements document | **Replace** with your own requirements |
| `pyproject.toml`, `main.py` | `uv` scaffold, not used by the pipeline | Ignore |

## Quick start: use this pipeline for your app

1. **Copy** `.github/workflows/kane-assurance.yml` and the `.testmuai/...` lines from `.gitignore`
   into your repo.
2. **Add the two platform secrets**. See [Setup](#setup).
3. **Design tests** for your app locally. See [Designing tests](#designing-tests-local). Make
   sure credentials and environment URLs appear as `{{placeholders}}`, not literal values.
4. **Supply every placeholder**: non-secret values in `kane-variables.seed.json`, private ones as
   `KANE_VAR_<NAME>` repository secrets. See [Credentials and test data](#credentials-and-test-data).
5. **Allow the workflow to push** the `test-results` branch (Settings → Actions → General →
   Workflow permissions → *Read and write permissions*).
6. **Commit and push** the `_test.md` files. The push runs the tests you changed. Or go to
   Actions → *Kane CLI Assurance* → *Run workflow* and pick `scope: all`.

## Setup

### Platform secrets (required)

Settings → Secrets and variables → Actions → **Secrets** → *New repository secret*:

| Secret | Where to get it |
|---|---|
| `LT_USERNAME` | TestMu AI / LambdaTest profile |
| `LT_ACCESS_KEY` | TestMu AI / LambdaTest profile |

The workflow uses these to log `kane-cli` in non-interactively.

### Workflow permissions

The `publish-results` job commits to a `test-results` branch, so `GITHUB_TOKEN` needs write
access: Settings → Actions → General → Workflow permissions → **Read and write permissions**.
If you'd rather not publish a results branch, delete the `publish-results` job. The job summary
and the `all-results` artifact still carry everything.

## Credentials and test data

### How placeholders resolve

A test step writes `{{name}}` wherever a value should be supplied at run time:

```markdown
## Step 1
Open {{login_url}} and sign in with username {{standard_user}} and password {{standard_password}}.
```

Before the tests run, each runner builds `.testmuai/variables/runtime.json`, which `kane-cli`
reads. The sources are merged in this order, and a later source wins:

| # | Source | Becomes | Use it for |
|---|---|---|---|
| 1 | `kane-variables.seed.json` (committed) | `{{name}}` as written | Values that aren't sensitive: public URLs, product names, search terms, deliberately invalid credentials |
| 2 | Actions **variables** named `KANE_VAR_<NAME>` | `{{name}}` | Per-repo config you don't want in code but that isn't secret, such as a staging URL |
| 3 | Actions **secrets** named `KANE_VAR_<NAME>` | `{{name}}`, marked `secret: true` | Usernames, passwords, API tokens, OTP seeds |
| 4 | The `login_url` workflow input | `{{login_url}}` and `{{base_url}}` | A one-off run against a different environment |

`<NAME>` is the placeholder name in upper case: `KANE_VAR_STANDARD_PASSWORD` supplies
`{{standard_password}}`. The run log lists which placeholders were supplied and marks the
secret ones. Values are never printed.

### Option A: public or non-sensitive values in the seed file

This is what the example does, because the demo app publishes its credentials:

```json
{
  "login_url":        { "value": "https://qaplayground.com/bank/login" },
  "standard_user":    { "value": "standard_user" },
  "standard_password":{ "value": "bank_sauce" },
  "invalid_username": { "value": "not_a_real_user" }
}
```

Only do this when the values are already public, or are fake values that exist only for testing.

### Option B: private credentials as GitHub secrets

This is the normal case for a real application.

**1. Use placeholders in the tests.** Never write a real credential into a `_test.md`:

```markdown
## Step 1
Open {{login_url}} and sign in with username {{app_user}} and password {{app_password}}.

## Step 2 @verifies ac-3
Assert the account dashboard is shown and displays {{app_user}}'s name.
```

**2. Keep secrets out of the seed file.** It holds only what's safe to commit:

```json
{
  "login_url":        { "value": "https://staging.your-app.com/login" },
  "invalid_username": { "value": "not_a_real_user" },
  "invalid_password": { "value": "wrong_password" }
}
```

Don't add placeholder entries such as `"app_password": { "value": "CHANGEME" }`. If the secret
were ever missing, the test would silently run with `CHANGEME`. When a key is absent, the
preflight check stops the run instead and names the missing secret.

**3. Add one repository secret per credential.** Go to Settings → Secrets and variables → Actions
→ Secrets → *New repository secret*:

| Secret name | Supplies |
|---|---|
| `KANE_VAR_APP_USER` | `{{app_user}}` |
| `KANE_VAR_APP_PASSWORD` | `{{app_password}}` |

Or use the GitHub CLI. Leaving out `--body` makes it prompt for the value, so the value doesn't
end up in your shell history:

```bash
gh secret set KANE_VAR_APP_USER
gh secret set KANE_VAR_APP_PASSWORD
gh variable set KANE_VAR_LOGIN_URL --body "https://staging.your-app.com/login"   # non-secret → Actions variable
```

**4. Run it.** On the runner, `runtime.json` ends up as:

```json
{
  "login_url":    { "value": "https://staging.your-app.com/login", "secret": false },
  "app_user":     { "value": "•••", "secret": true },
  "app_password": { "value": "•••", "secret": true }
}
```

GitHub masks secret values in the Actions log, and `secret: true` makes kane-cli mask them in its
own logs.

### Converting tests that have literal credentials

If your tests were designed with literal values, as the example's are ("sign in as frozen_user
with password bank_sauce"), swap the literals for placeholders:

```diff
- Open https://qaplayground.com/bank/login in the browser and sign in as frozen_user with password bank_sauce …
+ Open {{login_url}} in the browser and sign in as {{frozen_user}} with password {{frozen_password}} …
```

Then remove those values from the seed file and add them as `KANE_VAR_FROZEN_USER` /
`KANE_VAR_FROZEN_PASSWORD` secrets. On the next run, the edited step and every step after it in
that file are re-authored, because kane-cli only replays a step whose text is unchanged.

To get placeholders from the start, tell the designer before you design. Put this in
`.testmuai/context.md`:

```markdown
## Test data
- Never write credentials or environment URLs literally in a test. Use placeholders.
- The login page is {{login_url}}.
- "a valid user" / "valid existing credentials" means {{app_user}} / {{app_password}}.
- "an admin" means {{admin_user}} / {{admin_password}}.
```

### The preflight check

`kane-cli` doesn't check placeholders before it runs, so a missing secret would otherwise show up
as a confusing failure in the middle of a test. Each runner therefore scans its tests before
starting a browser and fails straight away:

```
Error: {{app_password}} has no value. Add it to kane-variables.seed.json, or as a repository secret/variable named KANE_VAR_APP_PASSWORD.
```

The check skips names a test defines itself, such as `save the response as order` →
`{{order.status}}`, or a `variables:` key in the test's own front matter.

### Separate credentials per environment

To keep different credentials for staging and production, use GitHub **Environments**:

1. Settings → Environments → create `staging` and `production`. Add the same `KANE_VAR_*` secret
   names to each, with that environment's values.
2. In the workflow, add an `environment` input and reference it in the `run-tests` job:

```yaml
on:
  workflow_dispatch:
    inputs:
      environment:
        type: choice
        options: [staging, production]
        default: staging
# …
jobs:
  run-tests:
    environment: ${{ inputs.environment || 'staging' }}
```

The environment's secrets override repository secrets that have the same name, and the variables
step picks them up with no other changes.

### Rules and caveats

- **Names:** GitHub stores secret and variable names in upper case, and the pipeline lower-cases
  them. Placeholders you supply through `KANE_VAR_*` must therefore be lower-case `snake_case`
  (`{{app_password}}`, not `{{appPassword}}`). Nested values (`{{tester.email}}`) can only come
  from the seed file.
- **Evidence shows the screen.** Password fields are obscured, but anything typed into a visible
  field, such as a username or an account number, appears in screenshots in the evidence packs.
- **The `test-results` branch is part of your repo.** Everyone with read access can see it. For a
  public repo with private test data, delete the `publish-results` job and rely on workflow
  artifacts, which you can restrict and which expire.
- **Use dedicated test accounts.** Don't use real customer or staff credentials, and rotate a
  secret by updating it in Settings. The next run picks it up.

## Designing tests (local)

```bash
npm install -g @testmuai/kane-cli
kane-cli login --oauth
kane-cli config set-url https://your-app.com/login

kane-cli context ingest requirements/your-app.md   # TTY drops you into the extract chat
kane-cli context list --type usecase               # what it derived
kane-cli context review                            # approve the use-cases (the human gate)
kane-cli design tests --use-case <uc-id>           # writes .testmuai/tests/*_test.md
kane-cli context fsck                              # check the lineage is intact
kane-cli cover gaps --stage design                 # which use-cases still have no tests (no model call)
```

Try a test locally before you commit it. Put your local credentials in
`.testmuai/variables/local.json`, which is gitignored:

```bash
kane-cli testrun run .testmuai/tests/<name>_test.md
```

Then commit `.context/` and `.testmuai/tests/`.

## Running the pipeline

### Triggers

- **Push to `main`** that touches `.testmuai/tests/**/*_test.md`: runs only the test files that
  push added or changed.
- **Manual** (Actions → *Kane CLI Assurance* → *Run workflow*):

| Input | Default | Meaning |
|---|---|---|
| `scope` | `changed` | `changed`: files changed in the last commit · `all`: every `_test.md` · `select`: only `test_files` |
| `test_files` | — | For `scope=select`: comma- or newline-separated paths from the repo root. A typo fails the run before any runner starts. |
| `login_url` | — | Overrides `{{login_url}}` and `{{base_url}}` for this run |
| `shard_count` | `2` | Parallel GitHub runners |
| `parallel_per_shard` | `4` | `kane-cli testrun --parallel` workers on each runner |

### Jobs

1. **`select-tests`** resolves the scope once and hands the same list to every shard.
2. **`run-tests`** is a matrix over the shards. Each runner installs kane-cli and Chrome, logs in,
   builds the variables, runs the preflight check, then runs its share of the tests as one
   execution:
   ```bash
   kane-cli testrun run <files> --parallel 4 --headless --on-failure continue
   ```
   It uploads its evidence pack plus each test's `Result.md` and generated automation code.
3. **`aggregate`** merges the shards into the `all-results` artifact and writes a passed / failed
   count, plus every `Result.md`, into the job summary.
4. **`publish-results`** commits the run to the `test-results` branch:
   ```
   test-results/
   ├── README.md                  # history: passed / failed / other per run
   ├── latest/                    # the most recent run
   └── runs/<run_id>-<attempt>/   # the last 30 runs
   ```

### Failed tests don't fail the pipeline

A failed test is a result, not a pipeline error. When a test fails, the run stays **green** and
the failure is recorded in the evidence pack, its `Result.md` and the `test-results` branch. The
run also shows a warning annotation with the count, for example *"4 failed and 0 other test(s)"*.
`--on-failure continue` makes sure the rest of the shard still runs.

A run goes **red** only when the pipeline itself couldn't do its job:

| Red step | Meaning | Fix |
|---|---|---|
| *Login* | `LT_USERNAME` / `LT_ACCESS_KEY` are missing or wrong | Check the two platform secrets |
| *Preflight* | A test uses a `{{placeholder}}` that nothing supplies | Add the `KANE_VAR_<NAME>` secret the error names |
| *Run this shard* | `kane-cli testrun` stopped before it finished (it never reported `testrun_done`) | Read the log above the error |
| *Resolve test scope* | `scope=select` listed a file that doesn't exist | Fix the path |

`kane-cli testrun` itself exits 1 whenever any test fails. The run step works out which case it
is from whether kane-cli reported that the run finished.

To find out why a test failed:

1. **Job summary** of the run: expand the failed test's `Result.md`.
2. **`test-results/latest/`** on GitHub: the same files, browsable.
3. **Evidence pack**, with screenshots of every step: download `all-results`, then run
   `kane-cli evidence serve <pack>.evidence`.

Then decide whether the **app** is wrong (a real bug, so leave the test as it is and report the
bug) or the **test** is wrong (fix the step and commit, and the push re-runs only that file).

### Worth knowing

- **Every CI run authors from scratch.** Step recordings (`.testmuai/tests/output-*/`) are
  gitignored and not cached between runs, so CI runs the AI agent on every step every time. That
  is slower and costs more than replaying. Caching `.testmuai/tests/output-*` with
  `actions/cache`, keyed on the test files, would let later runs replay.
- **Each shard seals its own pack.** Combine them into one with
  `kane-cli evidence merge <pack-a> <pack-b> --run-id <id> --title "<title>"`, and check a pack
  with `kane-cli evidence validate <pack> --profile L1`.
- **Coverage is a local step.** `kane-cli cover --from <pack> gaps` shows which acceptance
  criteria have a designed test (*designed*) and which have a passing run (*proven*). `--from` is
  an option of `cover`, so it goes before `gaps`.

## Keeping tests in step with requirements

When the requirements change, re-ingest them and let kane-cli propose the updates. Don't edit
tests silently:

```bash
kane-cli maintain reconcile      # every proposed change is held as a review card
kane-cli maintain evolve <ref>   # re-design the affected use-case; untouched items are preserved
```

Nothing is committed without your verdict, and every test traces back through `@verifies` tags
to an acceptance criterion in the requirements.

---

**Versions:** commands checked against `@testmuai/kane-cli@0.8.11`. CI installs the latest
release, because `KANE_CLI_VERSION` in the workflow is unpinned. Once you've validated a
version, pin it (e.g. `@testmuai/kane-cli@0.8.11`), and run `kane-cli changelog` before you bump
it.
