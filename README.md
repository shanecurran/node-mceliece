# node-mceliece
Node.js Library for the Post-Quantum McEliece Cryptosystem. Built for [qCrypt](https://qcry.pt/)

## Install
```bash
npm install mceliece
```

## Usage

```javascript
var mceliece    = require("mceliece");

// Generate a keypair (public key and private key)
var keyPair     = mceliece.keyPair();

// I would recommend converting data to Base64 beforehand to allow for non-UTF8 support
var plaintext   = "Hello world!";

// Convert the standard JavaScript string to a UTF8 Array
// All data encrypted must be a UTF8 Array
var utf8_array  = new Uint8Array(mceliece.stringToUTF8Array(plaintext));

// Encrypt the data
var encrypted   = mceliece.encrypt(utf8_array, keyPair.publicKey);

// Decrypt the data
var decrypted   = mceliece.decrypt(encrypted, keyPair.privateKey); // Should be the same as original

// Convert the decrypted UTF8 array back to a string
var decrypted_plaintext = mceliece.UTF8ArraytoString(decrypted);
```