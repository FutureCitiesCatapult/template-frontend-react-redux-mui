# template-frontend-react-redux-mui
This template project is designed to allow for the quick setup of a [React](https://reactjs.org/) with [Redux](https://redux.js.org/) ([React Redux](https://react-redux.js.org/)) project using the [Material UI](https://material-ui.com/) framework and [Webpack](https://webpack.js.org/) for bundling the code.

## Table of Contents:
- [template-frontend-react-redux-mui](#template-frontend-react-redux-mui)
  - [Table of Contents:](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Setup](#setup)
  - [Babel & Webpack Configuration](#babel--webpack-configuration)
    - [Configuration using Environment Variables](#configuration-using-environment-variables)
    - [Babel Configuration](#babel-configuration)
    - [Development and Production Build Modes](#development-and-production-build-modes)
      - [Development Builds](#development-builds)
      - [Production Build](#production-build)
  - [Unit Testing](#unit-testing)
  - [Docker Deployment](#docker-deployment)

## Prerequisites
The following tools are required to set up or run this template:
- [node](https://nodejs.org/) v10.15.3
- [npm](https://www.npmjs.com/) v6.4.1 **or** [Yarn](https://yarnpkg.com/) v1.16.0 

## Setup
1. Clone the repo from https://github.com/FutureCitiesCatapult/template-frontend-react-redux-mui.git.
2. Navigate to the root directory of this new repo and run either of the commands below:
```shell
// with npm
npm run setup

// with yarn
yarn run setup
```
 This `setup` script installs all of the required node packages in the root *node_modules* directory then scans for any vulnerabilities within the package files and automatically installs any compatible updates to vulnerable dependencies that were found. 
 
 A blank *.env* file is also created in the root directory (more on environment variables [here](#configuration-using-environment-variables)).

## Babel & Webpack Configuration

### Configuration using Environment Variables
The *webpack.config.js* uses the [dotenv-webpack](https://www.npmjs.com/package/dotenv-webpack) plugin alongside [dotenv-defaults](https://www.npmjs.com/package/dotenv-defaults) to expose any environment variables set in the *.env* or *.env.defaults* file in the root directory. These variables are available within the webpack configuration itself and also anywhere within the application in the format `process.env.[VARIABLE]`.

The root *.env.defaults* file must only contain non-sensitive configuration variables and should be considered safe to commit to any version control system.

Any sensitive details, such as passwords or private keys, should be stored in the root *.env* file. This file should **never** be committed and accordingly is already listed within the root *.gitignore* file. The *.env* file also serves to overwrite any non-sensitive variables defined within the root *.env.defaults* file.

### Babel Configuration
This project uses [Babel](https://babeljs.io/) to convert, transform and polyfill ECMAScript 2015+ code into a backwards compatible version of JavaScript.

As with *webpack.config.js* the environmental variables defined in *.env.defaults* and *.env* are available within the *babel.config.js* where Babel's configuration is programmatically created. 

### Development and Production Build Modes
In *webpack.config.js* there's a common configuration object for both `development` and `production` builds called `commonConfig` which mainly handles loading for various file types. Extend this object with any modules or plugins which apply to both build modes.

Within a switch statement after the `commonConfig` object individual properties for both the `development` and `production` builds can be defined separately as needed.

Webpack will use the `--mode` flag it recieves when run to determine which build to bundle. This flag defaults to `development`.

#### Development Builds
A `development` build can be run in the following ways:
```shell
// with npm
npm run dev
// or
npm run dev:hot

// with yarn
yarn run dev
// or
yarn run dev:hot
```
Both the `dev` and `dev:hot` scripts use [webpack-dev-server](https://webpack.js.org/configuration/dev-server/) to serve a `development` build locally. Some options are configured already in the root *.env.defaults* and can be overriden in the root *.env* file or within the root *webpack.config.js* itself as required.

#### Production Build
A `production` build can be run by the following command:
```
// with npm
npm run build

// with yarn
yarn run build
```
The `build` script will write an optimized and compressed build to the 'build' directory. If a different directory is required it will mean changing the *.package.json*'s `clean` script as well as the `output.path` property of the *webpack.config.json* accordingly.

## Unit Testing
... **to be continued**

## Docker Deployment
... **to be continued**