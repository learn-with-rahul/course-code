# course-code

This repository contains a sample GitHub Actions workflow in `.github/workflows/first-workflow.yaml`.

## Workflow: First Workflow

This workflow is triggered on every `push` to the repository.

### Jobs

The workflow consists of three jobs:

1.  **`run-shell-commands`**
    *   **Runner:** `ubuntu-latest`
    *   **Description:** This job runs a sequence of shell commands.
    *   **Steps:**
        *   `echo a string`: Prints "hello world".
        *   `multiline command`: Prints the versions of Node.js and npm.

2.  **`parallel-job-macos`**
    *   **Runner:** `macos-latest`
    *   **Description:** This job runs in parallel with `run-shell-commands`.
    *   **Steps:**
        *   `view sw version`: Prints the macOS version information.

3.  **`dependent-job`**
    *   **Runner:** `windows-latest`
    *   **Dependency:** This job depends on the successful completion of the `run-shell-commands` job.
    *   **Description:** This job runs on a Windows environment and contains a step that is designed to fail.
    *   **Steps:**
        *   `echo string`: Prints "windows string" using PowerShell.
        *   `error-step`: Attempts to run a non-existent command, which will cause the job to fail. This is for demonstration purposes.

### Workflow Diagram

```
[push] -> [run-shell-commands] -> [dependent-job] (fails)
       |
       -> [parallel-job-macos]
```
