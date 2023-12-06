### 1.0.0 (2023-12-07)

##### Implemented Keyring Controller for Base Chain

- Added method to generate keyring
- Added method to restore a keyring
- Added method to add a new account to the keyring object
- Added method to export the private key of an address
- Added method to sign a transaction
- Added method to sign a message
- Added method to sign Typed Data (EIP-712)
- Added importWallet() to import account using privateKey.
- Added sign() to sign a message or transaction and get signature along with v,r,s.