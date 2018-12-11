# react-native-simple-env
Simple environment variables for react-native

## Goals
- [ ] Read environment variables from `.env*` files.
- [ ] Specify which env file to read from (i.e. `.env.staging`).
- [ ] Read environment variables exorted in the shell process.
- [ ] Tests!

## Installation
```bash
// yarn
$ yarn add react-native-simple-env

// npm
$ npm i react-native-simple-env
```

### Usage
RNSE imports any variables defined in the `.env` file, in addition to any system environment variables exported in the shell process that begin with `REACT_NATIVE_`.

```bash
// .env

REACT_NATIVE_API_URL=https://swapi.co/api/
SUCCESS_MESSAGE='It still works'
```

```js
import {env} from "react-native-simple-env";

fetch(env.API_URL)
.then(() => console.log(env.SUCCESS_MESSAGE);
```

To specify which `.env` file to use, set the `RN_ENV` variable to the name of the file you want to use when starting the bundler.

```bash
$ RN_ENV=.env.staging react-native start`
```

### Precendence
1. Variables exported in the terminal process running the metro bundler.
2. Variables defined in `.env*` file.
