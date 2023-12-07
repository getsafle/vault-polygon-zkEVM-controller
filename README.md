# vault-polygon-zkEVM-controller <code><a href="https://www.docker.com/" target="_blank"><img height="50" src="https://zkevm.polygonscan.com/images/logo.svg?v=23.11.4.0"></a></code>

[![npm version](https://badge.fury.io/js/@getsafle%2Fvault-polygon-zkevm-controller.svg)](https://badge.fury.io/js/@getsafle%2Fvault-polygon-zkevm-controller)    <img alt="Static Badge" src="https://img.shields.io/badge/License-MIT-green">   [![Discussions][discussions-badge]][discussions-link]
 <img alt="Static Badge" src="https://img.shields.io/badge/Polygon zkEVM_controller-documentation-purple">    

A Module written in javascript for managing various keyrings of Polygon-zkEVM accounts, encrypting them, and using them.

- [Installation](#installation)
- [Initialize the Polygon-zkEVM Controller class](#initialize-the-polygon-zkevm-controller-class)
- [Methods](#methods)
  - [Generate Keyring with 1 account and encrypt](#generate-keyring-with-1-account-and-encrypt)
  - [Restore a keyring with the first account using a mnemonic](#restore-a-keyring-with-the-first-account-using-a-mnemonic)
  - [Add a new account to the keyring object](#add-a-new-account-to-the-keyring-object)
  - [Export the private key of an address present in the keyring](#export-the-private-key-of-an-address-present-in-the-keyring)
  - [Sign a transaction](#sign-a-transaction)
  - [Sign a message](#sign-a-message)
  - [Get balance](#get-balance)

## Installation
```
npm install --save @getsafle/vault-polygon-zkEVM-controller
```
## Initialize the Polygon-zkEVM Controller class

```
const { KeyringController, getBalance } = require('@getsafle/vault-polygon-zkEVM-controller');

const polygon_zkevmController = new KeyringController({
  encryptor: {
    // An optional object for defining encryption schemes:
    // Defaults to Browser-native SubtleCrypto.
    encrypt(password, object) {
      return new Promise('encrypted!');
    },
    decrypt(password, encryptedString) {
      return new Promise({ foo: 'bar' });
    },
  },
});
```

## Methods

### Generate Keyring with 1 account and encrypt

```
const keyringState = await polygon_zkevmController.createNewVaultAndKeychain(password);
```

### Restore a keyring with the first account using a mnemonic

```
const keyringState = await polygon_zkevmController.createNewVaultAndRestore(password, mnemonic);
```

### Add a new account to the keyring object

```
const keyringState = await polygon_zkevmController.addNewAccount(keyringObject);
```

### Export the private key of an address present in the keyring

```
const privateKey = await polygon_zkevmController.exportAccount(address);
```

### Sign a transaction

```
const signedTx = await polygon_zkevmController.signTransaction(polygon-zkevmTx, privateKey);
```

### Sign a message

```
const signedMsg = await polygon_zkevmController.signMessage(msgParams);
```

### Sign a message

```
const signedObj = await polygon_zkevmController.sign(msgParams, pvtKey, web3Obj);
```

### Sign Typed Data (EIP-712)

```
const signedData = await polygon_zkevmController.signTypedMessage(msgParams);
```

### Get balance

```
const balance = await getBalance(address, web3);
```
[discussions-badge]: https://img.shields.io/badge/Code_Quality-passing-rgba
[discussions-link]: https://github.com/getsafle/vault-polygon-zkevm-controller/actions
