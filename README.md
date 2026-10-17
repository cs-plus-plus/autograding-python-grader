# CS++ Autograding Python Grader

A maintained, drop-in continuation of [`classroom-resources/autograding-python-grader@v1`](https://github.com/classroom-resources/autograding-python-grader).
GitHub retired GitHub Classroom on 2026-08-28 and archived its autograding actions on 2026-09-04.
This repository keeps them working for teachers who grade in GitHub Actions, with or without
[CS++](https://csplusplus.com/github).

**To switch, change one line per step:**

```yaml
# before
uses: classroom-resources/autograding-python-grader@v1
# after
uses: cs-plus-plus/autograding-python-grader@v1
```

Inputs, outputs and results are identical to `classroom-resources/autograding-python-grader@v1`. The code is the original v1 release; this
fork changes only the action runtime (now Docker (unchanged)) and the action's name and author.
Issues and security reports: [open an issue](https://github.com/cs-plus-plus/autograding-python-grader/issues) or email
kevin@csplusplus.com.

Originally written by GitHub and released under the MIT License, which this fork keeps
(see `LICENSE.md`). It is not affiliated with or endorsed by GitHub.

---

## Original README (v1)

## GitHub Classroom Python Grader

### Overview
**GitHub Classroom Python Grader** is a plugin for GitHub Classroom's Autograder. Seamlessly integrate your CS class with GitHub using this action to facilitate the grading process.

### Key Features
- **Automatic Grading**: Evaluate student code submissions and provide immediate feedback.
- **Customizable Test Setup**: Define pre-test setup commands and specific testing commands.
- **Command Execution**: Run any command and determine the success based on the exit code.
- **Timeout Control**: Limit the runtime of tests to prevent excessive resource usage, with a maximum duration of 6 hours.
- **Scoring System**: Assign a maximum score for tests, awarding points upon successful test completion.

### Inputs

| Input Name      | Description                                                                                                     | Required |
|-----------------|-----------------------------------------------------------------------------------------------------------------|----------|
| `timeout`       | Duration (in minutes) before the test is terminated. Defaults to 10 minutes with a maximum limit of 6 hours.    | Yes      |
| `max-score`     | Points to be awarded if the test passes.                                                                        | No       |
| `setup-command`         | Command to execute prior to the test, typically for environment setup or dependency installation.                                                                | No       |

### Outputs

| Output Name | Description                        |
|-------------|------------------------------------|
| `result`    | Outputs the result of the grader, indicating the success or failure of the test.  |

### Usage

1. Add the GitHub Classroom Python Grader action to your workflow.

```
name: Autograding Tests

on:
  push

jobs:
  run-tests:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v4
    - name: Python test
      id: python-test
      uses: education/autograding-python-grader@v1
      with:
        timeout: '15'
        max-score: '100'
        setup-command: 'pip install -r requirements.txt'
    - name: Autograding Reporter
      uses: ...
```
