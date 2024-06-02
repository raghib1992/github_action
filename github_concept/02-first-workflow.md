# Workflow
### Step 1: Create Repo in github, name: gh-first-action
### Step 2: Create workflow file 
- gh-first-action/.github/workflows/first-action.yml
```yml
name: First Workflow
on: workflow_dispatch
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: Print greeitng
        run: echo "Hello World"
      - name: Print goodbye
        run: echo "Good Bye"
      - name: multi line step
        run: |
          echo "First line"
          echo "Second Line"
```
### Step 3: Run workflow in Action tab