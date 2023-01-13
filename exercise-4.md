<b>Exercise </b>
Recover the Public Key
When the signature is passed with all of its components (recovery bit included), the public key can be recovered. This means that blockchain nodes will be able to understand who signed the transaction that was sent to them. A transaction could indicate the user would like to send 1 ether to another address and provide a certain transaction fee. Since the signature signs the hash containing this intention, it is enough to authenticate this action entirely.

 Your Goal: Recover the Key
Given a message, signature, and recoveryBit find the public key and return it! Be sure to hash the message when passing it to the recovery method.
Use the noble-secp256k1 documentation to find the correct method and parameters for this one.

<b> Solution </b>
```
const secp = require("ethereum-cryptography/secp256k1");
const hashMessage = require("./hashMessage");

async function recoverKey(message, signature, recoveryBit) {
   return secp.recoverPublicKey(hashMessage(message), signature, recoveryBit)
}

module.exports = recoverKey;
```
