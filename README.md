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
- [**Yargs**](https://github.com/yargs/yargs): Built by [bcoe](https://github.com/bcoe), used by `webpack-cli`, `mocha`, `react-native`, `nyc`, and 14,343 other modules.
- [**arg**](https://github.com/zeit/arg): Built by [ZEIT](https://github.com/zeit), used by `now`, `ncc`, `micro`, `serve`, and many others. Key Feature: [tiny](https://packagephobia.now.sh/result?p=arg)

## Utility Libraries

### Performance Optimization

- [@babel/plugin-transform-modules-commonjs](https://github.com/react-native-community/cli/pull/152/) ([twitter tip](https://mobile.twitter.com/thymikee/status/1092885415365877760))

### Update Management/Nagging

- https://github.com/yeoman/update-notifier#readme

### Context/Config

**Context from filesystem/PATH**

- https://github.com/npm/node-which Like running `which`: Find the first instance of an executable in the PATH.
- https://github.com/szwacz/fs-jetpack filesystem access
- https://github.com/sindresorhus/find-up search up the parents path for where files are located

**Config validation**

- https://github.com/hapijs/joi used by React Native CLI for validation

**Loading/Storing config**

> ⚠️ Be aware of [the XDG spec](https://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html). Sindre's libraries use [`env-paths`](https://github.com/sindresorhus/env-paths#pathsconfig) to get paths compliant with this.

- https://github.com/sindresorhus/conf simple config storing (maybe try [conf-cli](https://github.com/natzcam/conf-cli) to manipulate if needed) the successor to [configstore](https://github.com/sindresorhus/conf#how-is-this-different-from-configstore)
- https://github.com/davidtheclark/cosmiconfig Find and load configuration from a package.json property, rc file, or CommonJS module. [Check `searchPaths` to implement XDG spec compliance.](https://github.com/davidtheclark/cosmiconfig/issues/152)
- https://github.com/jonschlinkert/data-store conf like datastore but in the shclinkerverse

### 🌟Input

- https://npm.im/enquirer (recommended)
- https://npm.im/inquirer
- https://npm.im/prompts
- https://npm.im/email-prompt

### Argument Parsing

- https://npm.im/meow
- https://npm.im/arg
- https://npm.im/minimist

> ⚠️ Your framework may come with parsing built in

### Command execution

- https://github.com/IndigoUnited/node-cross-spawn
- https://www.npmjs.com/package/execa

### Spinners

- https://npm.im/ora (recommended)
- https://www.npmjs.com/package/cli-ux#cliaction
- http://npm.im/log-update

### Templating

- https://www.npmjs.com/package/consolidate
- https://www.npmjs.com/package/ejs (Gluegun has this built in)
- https://github.com/amwmedia/plop
- Angular Schematics https://angular.io/guide/schematics
- Yeoman generator https://yeoman.io/

### 🌟Output

**Coloring**

- https://npm.im/chalk (recommended)
- https://npm.im/kleur
- https://npm.im/cfonts

**Boxing**

- https://npm.im/boxen
- https://www.npmjs.com/package/sign-bunny

**Tables**

- https://www.npmjs.com/package/cli-table
- https://www.npmjs.com/package/cli-ux#clitable

**Banners**

- https://github.com/patorjk/figlet.js

**Debug Logging*

- https://www.npmjs.com/package/debug (note that you might not need this, Node's inbuilt [`util.debuglog`](https://nodejs.org/api/util.html#util_util_debuglog_section) does a lot of the same h/t [@stefanjudis](https://twitter.com/stefanjudis/status/1148232306735362056))
- [React Native CLI has very simple logging](https://github.com/react-native-community/cli/blob/3f116721eb30071b04a2957f8bd02a81954699de/packages/tools/src/logger.ts) with verbose mode you can still with just chalk dependency

### Plugin/Release Management

- https://www.npmjs.com/package/live-plugin-manager
- https://www.npmjs.com/package/pacote (used in npm cli)
- https://www.npmjs.com/package/gh-release-fetch (very low level pull from github)

> ⚠️ None of these are offline-first. Keen on finding one that respects offline first.

### Dependency installs and Upgrading Scaffolds

- [make dependency installs silent!](https://github.com/react-native-community/cli/pull/292/files#diff-e24c0f8cadacd6e6b19fb64414998d99R78)
- [`upgrade` command based on git diffs](https://github.com/react-native-community/cli/pull/348)

### Misc

- https://npm.im/stmux for `tmux` like UI
- https://npm.im/listr for progress lists
- https://www.npmjs.com/package/cli-ux general Heroku CLI utils including OS notification
- https://github.com/jeroenouw/cgx Generate all the recommended files (pre-filled) for the Github community standards. (Issue templates, code of conduct, etc)
- https://github.com/zeit/pkg#readme packaging as executable (so no requirement for node or npm)
- https://github.com/kefranabg/readme-md-generator generate READMEs


## Beginner Tutorials

- https://www.twilio.com/blog/how-to-build-a-cli-with-node-js
