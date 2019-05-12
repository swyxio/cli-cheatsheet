# cli-cheatsheet
helpful libraries and resources for *building* Node.js CLIs. Not [a list of CLIs](https://github.com/agarrharr/awesome-cli-apps).

## Beginner Tutorials

- https://www.twilio.com/blog/how-to-build-a-cli-with-node-js

## Frameworks

- **Commander**  
  https://github.com/tj/commander.js/
  Built by TJ, used in `create-react-app`, `vue-cli`, and many others. Key feature: pluggability.
  
- **Oclif**  
  https://github.com/oclif/oclif
  Built by Heroku, used in [Heroku](https://github.com/heroku/cli) and [Salesforce](https://developer.salesforce.com/tools/sfdxcli) CLI's. Key feature: pluggability.
  
- **Sade**  
  https://github.com/lukeed/sade
  Built by lukeed, used in [tsdx](https://github.com/palmerhq/tsdx). Key feature: lightweight?
  
- **Gluegun**  
  https://github.com/infinitered/gluegun
  Built by Infinite Red, used in [Ignite](https://github.com/infinitered/ignite) and [AWS Amplify](https://github.com/aws-amplify/amplify-cli). Key feature: templating/filesystem
  
- **Ink**
  https://github.com/vadimdemedes/ink
  Built by Vadim & Sindre. Key Feature: React Components and Yoga Layout.

## Utility Libraries

### Prompting

- http://npm.im/enquirer (recommended)
- http://npm.im/inquirer
- https://npm.im/prompts
- http://npm.im/email-prompt

### {Color, Box, Table} Output

Coloring

- http://npm.im/chalk (recommended)
- https://npm.im/kleur

Boxing

- http://npm.im/boxen
- https://www.npmjs.com/package/sign-bunny

Tables

- https://www.npmjs.com/package/cli-table
- https://www.npmjs.com/package/cli-ux#clitable

### Spinners

- http://npm.im/ora (recommended)
- https://www.npmjs.com/package/cli-ux#cliaction

### Argument Parsing

- http://npm.im/meow
- http://npm.im/arg
- https://npm.im/yargs

### Command execution

- https://www.npmjs.com/package/execa

### Plugin/Release Management

- https://www.npmjs.com/package/live-plugin-manager
- https://www.npmjs.com/package/pacote (used in npm cli)
- https://www.npmjs.com/package/gh-release-fetch (very low level pull from github)

> ⚠️ None of these are offline-first. Keen on finding one that respects offline first.

### Misc

- http://npm.im/stmux for `tmux` like UI
- http://npm.im/listr for progress lists
- https://www.npmjs.com/package/cli-ux general Heroku CLI utils including OS notification

## CLI Design Thinking

- **12 Factor CLI Apps**  
  https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46
  Jeff Dickey's list of requirements for UX. [Talk version here](https://www.youtube.com/watch?v=Izx3-KSuaM8).

- **Heroku CLI Style Guide**  
  https://devcenter.heroku.com/articles/cli-style-guide
  Heroku's CLI Style Guide

