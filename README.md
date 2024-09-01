# GAWG Validate Build

This GitHub Action belongs to the GAWG workflow and is used to validate the configurations, Dockerfile, secrets, deployment, and runner.

## Author

Álvaro García Pizarro

## Inputs

- **technology** (string): Technology to validate. For example, nodejs, python, etc.
- **docker** (boolean): Flag to validate the Dockerfile. Default: `false`.
- **self-hosted-runner** (boolean): Flag to validate the self-hosted runner. Default: `false`.
- **deployment** (string): Deployment type. For example, kubernetes, helm, etc.

## Usage

```yaml
name: GAWG Validate Build

on: [push]

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: GAWG Validate Build
        uses: ./
        with:
          technology: 'nodejs'
          docker: true
          self-hosted-runner: false
          deployment: 'kubernetes'# gawg-validate-build
```

## Steps

1. **GAWG Information**:
   - Prints information about the action and the inputs provided.

2. **Technology Validation**:
   - Validates the presence of necessary files for the specified technology (e.g., `package.json` for Node.js, `requirements.txt` for Python, `pom.xml` for Java).

3. **Dockerfile Validation**:
   - Checks if a `Dockerfile` is present if Docker validation is enabled.

4. **Self-hosted Runner Validation**:
   - Checks if the necessary technology commands are installed on the self-hosted runner.

5. **Secrets Validation**:
   - Validates the presence of the `TEST_SECRET` secret.

6. **Deployment Validation**:
   - Placeholder for deployment validation.

7. **Summary**:
   - Prints a summary of the validation results, including the person who triggered the workflow, the branch used, the trigger event, the workflow run ID, and the execution time.

## Note

This action is meant to be used only privately by a GAWG workflow. 

## Example Output

```yaml
🎉 All validations passed successfully! | Technology: nodejs, Docker enabled: true, Self-hosted runners: false, Deployment type: kubernetes
👤 Workflow triggered by: github_actor
🔀 Branch: github_ref
⚡ Trigger: github_event_name
🆔 Workflow run ID: github_run_id
🕒 Execution time: date