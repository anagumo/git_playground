# Project Git
Project git is a repo to practice with git and tools to automatize a workfllow

## Commitlint
Commitlint is a tool to lint every commit message on `pre-commit`, it follows the conventional commits documentation.

To connfigure follow these instructions:
1. Create a new `package.json` file into your project folder to add local dependencies:

`touch package.json`

2. Install the **commitlint** package into your project, this should create a `commitlint.config.json` file to set some rules to lint your commits:

`npm install --save-dev @commitlint/{cli,config-conventional}`

3. Configure commitlint to use the conventional commits config:

`echo "module.exports { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js`

4. Now, to be able to lint every commit message before they are created without doing it manually, we need to configure a Git Hook, that is a way to run scripts automatically inside a repo. To use **commitlint** we need to setup the `commit-msg` hook, let's do it using Husky's:

`npm install --save-dev husky`

5. Then setup Husky into your project, it creates the `pre-commit` script in the `./husky` folder and updates the `prepare` script in `package.json`:

`npx husky init`

6. To add commit messages linting to commit-msg hook, try the follow:

`echo "npx --no -- commitlint --edit \$1" > .husky/commit-msg`

7. Now test it:

Fail: `git commit -m "Keep calm and commit"`

Success: `git commit -m "style: Keep calm and commit"`