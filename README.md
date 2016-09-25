# node-mceliece
Node.js Library for the Post-Quantum McEliece Cryptosystem

## Usage

```javascript
var mceliece    = require("mceliece");

// Generate a keypair (public key and private key)
var keyPair     = mceliece.keyPair();

// Convert a standard JavaScript string to a UTF8 Array
// All data encrypted must be a UTF8 Array
// I would recommend converting data to Base64 beforehand to allow for non-UTF8 support
var plaintext   = new Uint8Array(mceliece.stringToUTF8Array("Hello world!"));

// Encrypt the data
var encrypted   = mceliece.encrypt(plaintext, keyPair.publicKey);

// Decrypt the data
var decrypted   = mceliece.decrypt(encrypted, keyPair.privateKey); // Should be the same as original
```