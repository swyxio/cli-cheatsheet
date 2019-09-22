# cli-cheatsheet
helpful libraries and resources for *building* Node.js CLIs. Not [a list of CLIs](https://github.com/agarrharr/awesome-cli-apps).

## CLI Design Thinking

- **12 Factor CLI Apps** ([Blogpost](https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46), [Talk](https://www.youtube.com/watch?v=Izx3-KSuaM8)): Jeff Dickey's list of requirements for UX.

- **Heroku CLI Style Guide** ([Guide](https://devcenter.heroku.com/articles/cli-style-guide), [Talk](https://www.youtube.com/watch?v=PHiDG-_XoRk), [Talk](https://www.youtube.com/watch?v=a6ud5MkVN_s)): Heroku's CLI Style Guide. 

- **CLI State Machines** ([Gist](https://gist.github.com/sw-yx/3af1e264b8460af8897768045b2c229f)): My little thoughts on state management

- **Add a dry run mode for expensive commands** like [gatsby dry-run](https://github.com/gatsbyjs/gatsby/issues/16384)
  
## Frameworks

- [**Commander**](https://github.com/tj/commander.js/): Built by TJ, used in `create-react-app`, `vue-cli`, and many others. Key feature: pluggability. [**Vorpal**](https://github.com/dthree/vorpal) is another framework inspired by Commander and is seeking maintainers
- [**Oclif**](https://github.com/oclif/oclif): Built by Heroku, used in [Heroku](https://github.com/heroku/cli) and [Salesforce](https://developer.salesforce.com/tools/sfdxcli) CLI's. Key feature: pluggability.
- [**Sade**](https://github.com/lukeed/sade): Built by lukeed, used in [tsdx](https://github.com/palmerhq/tsdx). Key feature: lightweight?
- [**Gluegun**](https://github.com/infinitered/gluegun): Built by Infinite Red, used in [Ignite](https://github.com/infinitered/ignite) and [AWS Amplify](https://github.com/aws-amplify/amplify-cli). Key feature: templating/filesystem
- [**Ink**](https://github.com/vadimdemedes/ink): Built by Vadim & Sindre. Key Feature: React Components and Yoga Layout. See also [import-jsx](https://npm.im/import-jsx)
- [**Scritch**](https://github.com/jamiebuilds/scritch): Built by Jamie, used at Eventbrite. Key Feature: compose multiple scripts regardless of language into one CLI.
- [**Yargs**](https://github.com/yargs/yargs): Built by [bcoe](https://github.com/bcoe), used by `webpack-cli`, `mocha`, `react-native`, `nyc`, and 14,343 other modules.
- [**arg**](https://github.com/zeit/arg): Built by [ZEIT](https://github.com/zeit), used by `now`, `ncc`, `micro`, `serve`, and many others. Key Feature: [tiny](https://packagephobia.now.sh/result?p=arg)
- [**cac**](https://github.com/cacjs/cac): Built by [Egoist](https://github.com/egoist), used by `create-nuxt-app` and many others.

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
- https://www.npmjs.com/package/resolve to simulate Node `require.resolve`
  - https://www.npmjs.com/package/relative generate relative filepaths e.g. `relative('a/b/c', 'a/d') // ../../d`
- if dealing with yarn workspaces: https://www.npmjs.com/package/find-yarn-workspace-root
- File watching
  - https://www.npmjs.com/package/cpx (copying with watch functionality)
  - https://www.npmjs.com/package/chokidar (recommended)
  - [Sapper Watcher](https://github.com/sveltejs/sapper/blob/845c54bf8fa470756d5670408a112596a04ba9cc/src/api/dev.ts)
    - https://www.npmjs.com/package/cheap-watch
  - [VSCode's per-platform watchers](https://github.com/Microsoft/vscode/tree/61587049cb6f0801d8f1c6d6a612c7ab71fc7113/src/vs/workbench/services/files/node/watcher)
- File finding
  - https://www.npmjs.com/package/glob (dominant)
  - https://www.npmjs.com/package/glob-fs
  - https://www.npmjs.com/package/file-regex


**Config validation**

- https://github.com/hapijs/joi used by React Native CLI for validation
- https://www.npmjs.com/package/jest-validate from Jest but not Jest specific

**Loading config from json, rc file, etc***

- https://github.com/DavidWells/configorama
- https://github.com/davidtheclark/cosmiconfig Find and load configuration from a package.json property, rc file, or CommonJS module. [Check `searchPaths` to implement XDG spec compliance.](https://github.com/davidtheclark/cosmiconfig/issues/152)

*don't need but nice to know: https://www.npmjs.com/package/read-package-json*

**Loading/Storing config from a persistent store**

> ⚠️ Be aware of [the XDG spec](https://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html). Sindre's libraries use [`env-paths`](https://github.com/sindresorhus/env-paths#pathsconfig) to get paths compliant with this.

- https://github.com/sindresorhus/conf simple config storing (maybe try [conf-cli](https://github.com/natzcam/conf-cli) to manipulate if needed) the successor to [configstore](https://github.com/sindresorhus/conf#how-is-this-different-from-configstore)
- https://github.com/jonschlinkert/data-store conf like datastore but in the shclinkerverse

### 🌟Input

- https://npm.im/enquirer (recommended)
- https://npm.im/inquirer
- https://npm.im/prompts
- https://npm.im/email-prompt

**Stdin Parsing**

- https://npm.im/get-stdin (eg when you want to receive pipe results `cat mydata.json | mycli`)

**Argument Parsing**

- https://npm.im/meow
- https://npm.im/arg
- https://npm.im/minimist (hasn't been updated in a while though)
  - https://www.npmjs.com/package/cliclopts

> ⚠️ Your framework may come with parsing built in

**Input/Stdin/Argument Processing**

make sure to also normalize inputted stuff before you compare

- `path.resolve(str1) === path.resolve(str2)`
- https://npm.im/normalize-url
- https://github.com/sindresorhus/compare-urls

### 🌟Processing

**Command execution**

- https://github.com/IndigoUnited/node-cross-spawn
- https://www.npmjs.com/package/execa (recommended)

Sometimes processes can spawn processes. This is troublesome for watch/reload features. Kill them all with [`tree-kill`](https://www.npmjs.com/package/tree-kill).

You'll probably also use these in conjunction with port monitors (e.g. the process you're working with opens a port, like CRA for [Netlify Dev](https://github.com/netlify/netlify-dev-plugin/)):

- https://github.com/Rich-Harris/port-authority#readme
- https://github.com/mikeal/getport#readme
- https://github.com/sindresorhus/get-port#readme

If child_processes are going to be a key part of your CLI, be sure to [read the docs](https://nodejs.org/api/child_process.html) and [this guide](https://www.freecodecamp.org/news/node-js-child-processes-everything-you-need-to-know-e69498fe970a/) to be aware of the API.

**Spinners**

- https://npm.im/ora (recommended)
- https://www.npmjs.com/package/cli-ux#cliaction
- http://npm.im/log-update

**Templating**

- https://www.npmjs.com/package/consolidate
- https://www.npmjs.com/package/ejs (Gluegun has this built in)
- Mustache and handlebars https://www.npmjs.com/package/handlebars
- Liquid templating (from Shopify) https://github.com/Shopify/liquid
- https://github.com/amwmedia/plop
- Angular Schematics https://angular.io/guide/schematics
- Yeoman generator https://yeoman.io/

**Temp folders**
- https://www.npmjs.com/package/tempy (create unique temp directories)
- https://www.npmjs.com/package/tmp (very popular. can remove on exit)

### 🌟Output

**Files**

- ensure directory exists: https://stackoverflow.com/questions/13542667/create-directory-when-writing-to-file-in-node-js
- encrypt files: https://medium.com/@brandonstilson/lets-encrypt-files-with-node-85037bea8c0e

**Coloring**

- https://npm.im/chalk (recommended - also see [Related Packages](https://github.com/chalk/chalk#related))
- https://npm.im/kleur
- https://npm.im/cfonts
- https://npm.im/tinycolor2 (some interesting APIs, handy with React Ink)
- https://npm.im/log-symbols (colored xplatform unicode symbols for success/info/warning/error)

Note that you may want to offer the option to [FORCE_COLOR](https://twitter.com/swyx/status/1166431071711498240) in CI logging.

**PrettyPrinting**

- https://npm.im/pretty-bytes

**Boxing**

- https://www.npmjs.com/package/term-size Get Terminal Size
- https://npm.im/boxen
- https://www.npmjs.com/package/sign-bunny

**Tables**

- https://www.npmjs.com/package/cli-table
- https://www.npmjs.com/package/cli-ux#clitable

**Banners**

- https://github.com/patorjk/figlet.js

**Debug Logging*

- https://www.npmjs.com/package/debug (note that you might not need this, Node's inbuilt [`util.debuglog`](https://nodejs.org/api/util.html#util_util_debuglog_section) does a lot of the same h/t [@stefanjudis](https://twitter.com/stefanjudis/status/1148232306735362056))
- https://github.com/winstonjs/winston
- https://github.com/trentm/node-bunyan
- [React Native CLI has very simple logging](https://github.com/react-native-community/cli/blob/3f116721eb30071b04a2957f8bd02a81954699de/packages/tools/src/logger.ts) with verbose mode you can still with just chalk dependency

### Plugin/Release Management

- https://www.npmjs.com/package/live-plugin-manager
- https://www.npmjs.com/package/pacote (used in npm cli)
- https://www.npmjs.com/package/gh-release-fetch (very low level pull from github)
- https://www.npmjs.com/package/require-package-name (get package names as if local files were modules)

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
- https://github.com/netlify/netlify-dev-plugin/pull/227/files disable clearing of screen like with React-Scripts
- https://github.com/DanWebb/jdown for parsing a directory of markdown files into json, just wonderful


## Beginner Tutorials

- https://www.twilio.com/blog/how-to-build-a-cli-with-node-js
