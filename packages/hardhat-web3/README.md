[![npm](https://img.shields.io/npm/v/@nomiclabs/hardhat-web3.svg)](https://www.npmjs.com/package/@nomiclabs/hardhat-web3)
[![hardhat](https://usehardhat.com/hardhat-plugin-badge.svg?1)](https://usehardhat.com)

# hardhat-web3

This plugin integrates [Web3.js](https://github.com/ethereum/web3.js) `1.x` into [Hardhat](http://gethardhat.com).

## What

This plugin brings to Hardhat the Web3 module and an initialized instance of Web3.

# Installation

```bash
npm install --save-dev @nomiclabs/hardhat-web3 web3
```

And add the following statement to your `hardhat.config.js`:

```js
usePlugin("@nomiclabs/hardhat-web3");
```

## Tasks

This plugin creates no additional tasks.

## Environment extensions

This plugin adds the following elements to the `HardhatRuntimeEnvironment`:

- `Web3`: The Web3.js module.
- `web3`: An instantiated Web3.js object connected to the selected network.

## Usage
Install it and access Web3.js through the Hardhat Runtime Environment anywhere you need it (tasks, scripts, tests, etc). For example, in your `hardhat.config.js`:
```
usePlugin("@nomiclabs/hardhat-web3");

// task action function receives the Hardhat Runtime Environment as second argument
task("accounts", "Prints accounts", async (_, { web3 }) => {
  
  console.log(await web3.eth.getAccounts());
  
});

module.exports = {};
```
And then run `npx hardhat accounts` to try it.

Read the documentation on the [Hardhat Runtime Environment](https://usehardhat.com/documentation/#hardhat-runtime-environment-hre) to learn how to access the HRE in different ways to use Web3.js from anywhere the HRE is accessible.

## TypeScript support

If your project uses TypeScript, you need to create a `hardhat-env.d.ts` file like this:

``` typescript
/// <reference types="@nomiclabs/hardhat-web3" />
```

If you already have this file, just add that line to it.


Then you have to include that file in the `files` array of your `tsconfig.json`:

```json
{
  ...
  "files": [..., "hardhat-env.d.ts"]
}
```

using the relative path from the `tsconfig.json` to your `hardhat-env.d.ts`.