# Nodejs

## Quick Start

```
npm init -y
npm install -D jest
npm test
npm install -D eslint
airbnb style guide
vscode -> eslint, prettier plugin
npm install -D eslint prettier eslint-plugin-prettier
npx install-peerdeps --dev eslint-config-airbnb-base
npm install uuid
npm install -D nodemon
node index.js
npm outdated
```

airbnb style guide

## Links

- openbase.com

## path

```javascript
const path = require('path');                    // path is a core module in nodejs.
console.log(__dirname);                          // Every common js module contains __dirname, __filename, module, require, export by default.
console.log(__filename);
console.log(path.basename(__filename));          // basename refers to file name
console.log(path.dirname(__filename));
console.log(path.extname(__filename));
```

## FAQ

### How to use jest for unit testing?

```
test
describe
```
vscode plugin: jest runner

### How to generate static swagger html?

```
npm i -g bootprint bootprint-openapi html-inline
bootprint openapi http://localhost:9090/icbc/amis/app/v2/api-docs swagger
html-inline swagger/index.html > iais_api.html
```
