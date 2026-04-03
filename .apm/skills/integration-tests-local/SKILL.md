---
name: integration-tests-local
description: Run integration tests locally when CI fails due to memory limits (exit code 137)
---

# Integration Tests — Local Run

CI integration tests run inside a WinCC OA Docker container. The container's memory limit can cause the test process to be killed (exit code 137). When this happens, CI posts a comment asking you to run the tests locally and paste the result into the PR.

## Trigger

You need to run locally when you see this comment on your PR:

```
⚠️ Integration Tests: Manual Confirmation Required
The integration tests were killed due to memory limits (exit code 137).

PR author: Please run integration tests locally and paste the result in the PR:

npm run test:integration
Copy the Local Integration Test Result block from the test output into this PR.
```

## Prerequisites

- WinCC OA licensed installation

## Run the Tests

```bash
npm run ci:integration
```

This command runs `npm ci && npm run compile && npm run test:integration` in one step.

If you only need to re-run tests without reinstalling:

```bash
npm run test:integration
```

## Post the Result to the PR

1. Find the block in the terminal output labeled **Local Integration Test Result**
2. Copy the entire block (including the block header/footer markers)
3. Paste it as a comment on the PR

The CI workflow will detect the comment and mark the integration check as passed.

## Alternatively: Re-trigger via Workflow Dispatch

Instead of commenting, you can re-run the CI workflow with manual confirmation:

1. Go to the PR → **Actions** tab → **CI/CD Pipeline**
2. Click **Run workflow**
3. Check ✅ **"I confirm that I have run all integration tests locally and they passed"**
4. Run

This marks the check as passed without requiring a comment.

## Why This Happens

GitHub-hosted runners have limited RAM. The WinCC OA process is memory-intensive and gets killed by the OS (OOM killer → exit code 137). Local machines or self-hosted runners with sufficient RAM do not have this problem.
