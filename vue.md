# Vue

## Quickstart

```bash
npm install -g vue-cli
vue --version
vue create <project_name:hello>
vue init webpack myapp
npm install
npm run serve
npm run serve -- --port 3000
npm run build
```

## Awesome Vue

- vuepress

## unit testing: Vue Test Utils & jest

```bash
vue add unit-jest
npm i -D @vue/test-utils
npm run test:unit -- -u      # -- means pass parameters to test:unit not npm, -u means update snapshot.
```

## e2e testing: Nightwatch

An integrated framework for end-to-end testing on web appliaitons across all major browsers.

```bash
npx nightwatch node_modules/nightwatch/examples/test/ecosia.js --env chrome
```

## e2e testing: cypres

```text
npm install cypress
```

## vue cli

```
vue inspect > ~/tmp/vue_inspect.txt
vue inspect --mode production > ~/tmp/vue_inspect.txt
vue inspect --plugins
vue inspect --rules
```

## FAQ

### How to use npx?

npx can help you to run applications in your node_modules but not in global.

```bash
npx chromedriver --help
```

### How to check current package version used in npm?

```
npm -v <package-name:vue>
npm list
```

### What are important environment variables in vue project?

- NODE_ENV: vue-cli-service have three default modes, including `development`, `test` and `production`. 
`vue-cli-service serve` use development mode, `vue-cli-service test:unit` use test mode, `vue-cli-service build` use
production mode. You can specify `--mode development` options to tell vue-cli-service to use specific mode in an action.

### How to check jest config in vue project?

```bash
npx jest --showConfig
```
