# Idol Hours — CI Harness

This is a **public** repository that exists solely to run CI validation for
[colorfulbutterflies/Idol-Hours](https://github.com/colorfulbutterflies/Idol-Hours) —
a **private** repository — on GitHub's free public-repository Actions minutes,
instead of the private repo's limited quota.

## What this repo is
- Two `workflow_dispatch`-only GitHub Actions workflows (`validate.yml`, `e2e.yml`).
- Nothing else. No application source, art, narrative, or documentation from
  Idol Hours lives here or is ever copied here.

## How it works
1. A trusted process (the repo owner's local machine, or the private repo's
   landing automation) dispatches `validate.yml` with a specific commit SHA
   from the private repo.
2. The workflow checks out that exact SHA using a fine-grained, read-only,
   single-repo access token stored as the `PRIVATE_REPO_TOKEN` secret.
3. It runs the same validation gate (typecheck, architecture check, unit
   tests, build, skills lint) the private repo would otherwise run on every push.
4. Only pass/fail status and safe build logs are produced — no private source
   is uploaded as an artifact, printed to logs, or otherwise exposed.

## What this repo is not
Not a mirror of Idol Hours. Not a place for issues/PRs/discussion about Idol
Hours content. Never runs untrusted code with `PRIVATE_REPO_TOKEN` — only
trusted `workflow_dispatch` runs.
