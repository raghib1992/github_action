# NodeJs app run locally in laptop
### Step 1: Download node js app locally
### Step 2: cd in to nodejs app folder
```
cd second-action-react-demo
```
### Step 3: Install npm
```
npm install
```
### Step 3: Run app
```
npm run dev
```
### Step 5: Verify in browser
```
http://localhost:5173
```

# Nodejs app workflow with multiple job run in parallel
```yml
name: Deploy Project
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Get-code
        uses: actions/checkout@v3
      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: Install dependencies
        run: npm ci
      - name: Run test
        run: npm test
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Get-code
        uses: actions/checkout@v3
      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: Install dependencies
        run: npm ci
      - name: Build Project
        run: npm run build
      - name: Deploy
        run: echo "deploying....."
```
# Nodejs app workflow with multiple job run in sequential
```yml
name: Deploy Project
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Get-code
        uses: actions/checkout@v3
      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: Install dependencies
        run: npm ci
      - name: Run test
        run: npm test
  deploy:
    need: test
    runs-on: ubuntu-latest
    steps:
      - name: Get-code
        uses: actions/checkout@v3
      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: Install dependencies
        run: npm ci
      - name: Build Project
        run: npm run build
      - name: Deploy
        run: echo "deploying....."
```
# Nodejs app workflow with multiple job run in sequential with multple trigger
```
name: Deploy Project
on: [push,workflow_dispatch]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Get-code
        uses: actions/checkout@v3
      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: Install dependencies
        run: npm ci
      - name: Run test
        run: npm test
  deploy:
    need: test
    runs-on: ubuntu-latest
    steps:
      - name: Get-code
        uses: actions/checkout@v3
      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 18
      - name: Install dependencies
        run: npm ci
      - name: Build Project
        run: npm run build
      - name: Deploy
        run: echo "deploying....."
```