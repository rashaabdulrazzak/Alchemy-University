<b>Exercise </b>

Signing the Hash
It's time to sign a message using our private key to prove our intention!

When signing a message with secp256k1 we can return the signature along with the recovery bit, allowing us to recover the public key from the signature. This will allow a blockchain node to take a signature of a transaction and understand which address authenticated this particular transaction.
 Your Goal: Sign Message
Let's sign a message!

First step is to hash it using the hashMessage function you created in the last stage (we've already imported it for you on line 2)
Once you have the message hash, use the sign method from ethereum-cryptography.
Note
The sign method will take your message hash along with the constant PRIVATE_KEY declared at the top of the file. This private key is a valid key that could be used to authorize blockchain transactions. Never use this specific key because it is published on the internet, so many people including yourself could authenticate with this specific private key. In future lessons we'll be discussing good private key hygene to avoid losing funds.
The ethereum-cryptography library uses noble-secp256k1, so the import comes from ethereum-cryptography but the detailed documentation is in the readme of noble-secp256k1.
The sign method takes an optional third parameter called options, which you'll see in the documentation. Use this parameter to return the recovered bit so that the public key can be recovered from this signature.

<b>Solution </b>
const secp = require("ethereum-cryptography/secp256k1");
const hashMessage = require('./hashMessage');

const PRIVATE_KEY = "6b911fd37cdf5c81d4c0adb1ab7fa822ed253ab0ad9aa18d77257c88b29b718e";

async function signMessage(msg) {
    const hashedMessage = hashMessage(msg);
    return secp.sign(hashedMessage, PRIVATE_KEY, { recovered: true })
}

module.exports = signMessage;
