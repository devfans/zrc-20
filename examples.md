# examples

Please understand that this is an experimental standard, and know how it works before testing. Use at your own risk. Examples of balance changing events. Wallets tested with: Xverse.

#### Mint 1 "ordi" to yourself <a href="#mint-1-ordi-to-yourself" id="mint-1-ordi-to-yourself"></a>

**ordi has already reached its maximum supply, example for demonstration purposes only.**

* Minter populates mint function with required information
* Inscribe the function to your own ordinal enabled wallet taproot address. **Make sure not using inscription service that mints to itself first.**

| User   | Balance at start | Balance at end |
| ------ | ---------------- | -------------- |
| Minter | 0                | 1              |

#### Transfer 500 "ordi" to Satoshi's wallet <a href="#transfer-500-ordi-to-satoshis-wallet" id="transfer-500-ordi-to-satoshis-wallet"></a>

Satoshi wallet just an example. Can send to any ordinal compatible taproot address.

* Populate transfer function with required information
* Inscribe the function to your own ordinal enabled wallets taproot address that holds the balance. **Make sure not using inscription service that mints to itself first. Some ordinal wallets generate a different address each time, make sure to send to the address that holds the balance.**
* Send the inscription from your wallet to Satoshi's ordinal enabled wallets taproot address (if he had one).
* Satoshi now has 500 "ordi"

| User    | Balance at start | Balance at end |
| ------- | ---------------- | -------------- |
| Sender  | 500              | 0              |
| Satoshi | 0                | 500            |

### VERY EXPERIMENTAL EXAMPLES, USE AT YOUR OWN RISK <a href="#very-experimental-examples-use-at-your-own-risk" id="very-experimental-examples-use-at-your-own-risk"></a>

Only included because people were getting scammed. Remember, these are worthless!

#### Trade 250 "ordi" for 1 sat via escrow <a href="#trade-250-ordi-for-1-sat-via-escrow" id="trade-250-ordi-for-1-sat-via-escrow"></a>

**Do not recommend trading until trusted balance state index tool is available. As it stands there is no easy way of accurately checking if the seller has a valid balance. Escrow trust/error risks should also be considered.**

* Seller populate transfer function with required information
* Seller inscribes the function to their own ordinal enabled wallet taproot address that holds the balance. **Make sure not using inscription service that mints to itself first. Some ordinal wallets generate a different address each time, make sure to send to the address that holds the balance.**
* Seller send's the inscription from their wallet to the escrows taproot address.
* Escrow checks **balance state index tool** to check their wallet has a valid balance
* Buyer sends 1 sat to escrows bitcoin address
* Escrow now has 1 sat and 250 "ordi"
* Escrow populate transfer function with required information
* Escrow inscribes the function to their own ordinal enabled wallet taproot address that holds the balance. **Make sure not using inscription service that mints to itself first. Some ordinal wallets generate a different address each time, make sure to send to the address that holds the balance.**
* Escrow send's the inscription from their wallet to the buyers taproot address.
* Escrow sends 1 sat to sellers bitcoin address

| User   | Balance at start | Balance at end |
| ------ | ---------------- | -------------- |
| Seller | 250              | 0              |
| Buyer  | 0                | 250            |

#### Trade 250 "ordi" for 1 wei via emblem vault <a href="#trade-250-ordi-for-1-wei-via-emblem-vault" id="trade-250-ordi-for-1-wei-via-emblem-vault"></a>

**Do not recommend trading until trusted balance state index tool is available. As it stands there is no easy way of accurately checking if the emblem vault has a valid balance.**

* Seller populate transfer function with required information
* Seller inscribes the function to their own ordinal enabled wallet taproot address that holds the balance. **Make sure not using inscription service that mints to itself first. Some ordinal wallets generate a different address each time, make sure to send to the address that holds the balance.**
* Seller creates emblem vault and populates title / description with transfer function details
* Seller mints the emblem vault
* Seller send's the inscription from their wallet to the emblem vaults taproot address.
* Emblem vault now has 250 "ordi"
* Seller lists emblem vault for 1 wei
* Buyer checks **balance state index tool** to check if emblem vault has valid balance
* Buyer buys emblem vault for 1 wei
* Buyer now has control of emblem vault. **If buyer wants to move balance from emblem vault**, buyer unlocks vault.
* Buyer imports private keys to an ordinal compatible wallet
* Buyer populates transfer function with required information
* Buyer inscribes the function to the imported ordinal enabled wallet taproot address that holds the balance. **Make sure not using inscription service that mints to itself first. Some ordinal wallets generate a different address each time, make sure to send to the address that holds the balance.**
* Buyer send's the inscription from their wallet to the desired destinations taproot address.
* Desired destination now has 250 "ordi"

| User   | Balance at start | Balance at end |
| ------ | ---------------- | -------------- |
| Seller | 250              | 0              |
| Buyer  | 0                | 250            |
