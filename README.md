## Pre config with CommitLint + Husky + CZ CLI

<a href="https://github.com/typicode/husky">
  <img src="https://img.shields.io/badge/github-huksy-blue?style=flat-square&logo=appveyor">
</a>

<a href="https://github.com/commitizen/cz-cli">
  <img src="https://img.shields.io/badge/github-czcli-red?style=flat-square&logo=appveyor">
</a>

<a href="https://github.com/conventional-changelog/commitlint">
  <img src="https://img.shields.io/badge/github-commitlint-green?style=flat-square&logo=appveyor">
</a>

<hr/>

<p align="center">
  <img width="600" src="https://raw.githubusercontent.com/conventional-changelog/commitlint/master/docs/assets/commitlint.svg?sanitize=true">
</p>


```
npm install husky --save-dev
```

```sh
# Install commitlint cli and conventional config
npm install --save-dev @commitlint/{config-conventional,cli}

# For Windows:
npm install --save-dev @commitlint/config-conventional @commitlint/cli

# Configure commitlint to use conventional config
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```


First, install the Commitizen cli tools:
```
npm install commitizen -g
```
Next, initialize your project to use the cz-conventional-changelog adapter by typing:

```
commitizen init cz-conventional-changelog --save-dev --save-exact
```

To lint commits before they are created you can use Husky's 'commit-msg' hook:

```json
"husky": {
  "hooks": {
    "commit-msg": "commitlint -E HUSKY_GIT_PARAMS",
    "prepare-commit-msg": "exec < /dev/tty && git cz --hook || true"
  }  
},
```

Try commit your project
```
git add -A; git commit
```

