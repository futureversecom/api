# @polkadot/api

This library provides a clean wrapper around all the methods exposed by a Polkadot/Substrate network client and defines all the types exposed by a node. For complete documentation around the interfaces and their use, visit the [documentation portal](https://polkadot.js.org/docs/api/).

If you are an existing user, please be sure to track the [CHANGELOG](CHANGELOG.md) when changing versions.

## tutorials

Looking for tutorials to get started? Look at [examples](https://polkadot.js.org/docs/api/examples/promise/) for guides on how to use the API to make queries and submit transactions.


## Create docs from metadata

yarn create:metadata --chain "root"
yarn create:metadata --chain "porcini"

Make sure to update the metadata at packages/types-support/src/metadata/v14/root-hex.ts and packages/types-support/src/metadata/v14/porcini-hex.ts after a runtime upgrade

Copy the docs created in the root folder to https://github.com/futureversecom/trn-docs/tree/main/docs
