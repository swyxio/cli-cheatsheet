# cli-cheatsheet
helpful libraries and resources for *building* Node.js CLIs. Not [a list of CLIs](https://github.com/agarrharr/awesome-cli-apps).

## CLI Design Thinking

- **12 Factor CLI Apps** ([Blogpost](https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46), [Talk](https://www.youtube.com/watch?v=Izx3-KSuaM8)): Jeff Dickey's list of requirements for UX.

- **Heroku CLI Style Guide** ([Guide](https://devcenter.heroku.com/articles/cli-style-guide), [Talk](https://www.youtube.com/watch?v=PHiDG-_XoRk), [Talk](https://www.youtube.com/watch?v=a6ud5MkVN_s)): Heroku's CLI Style Guide. 

- **CLI State Machines** ([Gist](https://gist.github.com/sw-yx/3af1e264b8460af8897768045b2c229f)): My little thoughts on state management
  
## Frameworks

- [**Commander**](https://github.com/tj/commander.js/): Built by TJ, used in `create-react-app`, `vue-cli`, and many others. Key feature: pluggability. [**Vorpal**](https://github.com/dthree/vorpal) is another framework inspired by Commander and is seeking maintainers
- [**Oclif**](https://github.com/oclif/oclif): Built by Heroku, used in [Heroku](https://github.com/heroku/cli) and [Salesforce](https://developer.salesforce.com/tools/sfdxcli) CLI's. Key feature: pluggability.
- [**Sade**](https://github.com/lukeed/sade): Built by lukeed, used in [tsdx](https://github.com/palmerhq/tsdx). Key feature: lightweight?
- [**Gluegun**](https://github.com/infinitered/gluegun): Built by Infinite Red, used in [Ignite](https://github.com/infinitered/ignite) and [AWS Amplify](https://github.com/aws-amplify/amplify-cli). Key feature: templating/filesystem
- [**Ink**](https://github.com/vadimdemedes/ink): Built by Vadim & Sindre. Key Feature: React Components and Yoga Layout.
- [**Scritch**](https://github.com/jamiebuilds/scritch): Built by Jamie, used at Eventbrite. Key Feature: compose multiple scripts regardless of language into one CLI.

## Utility Libraries

### Update Management/Nagging

- https://github.com/yeoman/update-notifier#readme

### Context/Configuration

- https://github.com/npm/node-which Like running `which`: Find the first instance of an executable in the PATH.
- https://github.com/szwacz/fs-jetpack filesystem access
- https://github.com/davidtheclark/cosmiconfig Find and load configuration from a package.json property, rc file, or CommonJS module

### 🌟Input

- https://npm.im/enquirer (recommended)
- https://npm.im/inquirer
- https://npm.im/prompts
- https://npm.im/email-prompt

### Argument Parsing

- https://npm.im/meow
- https://npm.im/arg
- https://npm.im/yargs
- https://npm.im/minimist

> ⚠️ Your framework may come with parsing built in

### Command execution

- https://github.com/IndigoUnited/node-cross-spawn
- https://www.npmjs.com/package/execa

### Spinners

- https://npm.im/ora (recommended)
- https://www.npmjs.com/package/cli-ux#cliaction

### Templating

- https://www.npmjs.com/package/consolidate
- https://www.npmjs.com/package/ejs (Gluegun has this built in)
- https://github.com/amwmedia/plop

### 🌟Output

**Coloring**

- https://npm.im/chalk (recommended)
- https://npm.im/kleur

**Boxing**

- https://npm.im/boxen
- https://www.npmjs.com/package/sign-bunny

**Tables**

- https://www.npmjs.com/package/cli-table
- https://www.npmjs.com/package/cli-ux#clitable

### Plugin/Release Management

- https://www.npmjs.com/package/live-plugin-manager
- https://www.npmjs.com/package/pacote (used in npm cli)
- https://www.npmjs.com/package/gh-release-fetch (very low level pull from github)

> ⚠️ None of these are offline-first. Keen on finding one that respects offline first.

### Misc

- https://npm.im/stmux for `tmux` like UI
- https://npm.im/listr for progress lists
- https://www.npmjs.com/package/cli-ux general Heroku CLI utils including OS notification


## Beginner Tutorials

- https://www.twilio.com/blog/how-to-build-a-cli-with-node-js
