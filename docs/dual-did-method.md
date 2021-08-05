# Dual DID Method Specification

## Dual DID

### Dual DID Method Name
The namestring which identifies this DID method is: `dual`.

### Dual DID Method Specific Identifier
This DID consists of "did:dual:" + "network-id:" + "identifier", and conforms to the requirements specified in the [DID specification](https://w3c.github.io/did-core/) currently published by the W3C Credentials Community Group.
`network-id` is the Ethereum chain id which is an identifier of the network. It is expressed in hexadecimal.
```
did:dual:0x420ada7:123456789abcdef123456789abcdef123456789abc
```

#### DID Document Example
```
{
    "@context": "https://w3id.org/did/v1",
    "id": "did:dual:0xea6328ef09549e48d4adadfcee4a8cb3a6fcdcf8",
    "publicKey": [
        {
            "id": "did:dual:0xea6328ef09549e48d4adadfcee4a8cb3a6fcdcf8#controller",
            "controller": "did:dual:0xea6328ef09549e48d4adadfcee4a8cb3a6fcdcf8",
            "type": "Secp256k1VerificationKey2018",
            "ethereumAddress": "0xea6328ef09549e48d4adadfcee4a8cb3a6fcdcf8"            
        }
    ],
    "service": [
        {
            "id": "did:dual:0xea6328ef09549e48d4adadfcee4a8cb3a6fcdcf8",
            "type": "smartidcard",
            "serviceEndpoint": "smartidcard.com/verify"
        }
    ]
}
```

## CRUD Operations

### Create

An Ethereum address is generated from a user's private key using secp256k1 used in Ethereum cryptography. This process runs regardless of the blockchain, and a DID document is created using Dual DID resolver if required.

### Read

Only deleted state for the DID can be verified from the blockchain.

### Update

Updating a DID document is not supported.

### Delete

In order to delete the DID, Dual DID API is used.

## Security Considerations

- Verifiable Credentials contain the holder's DID for non-repudiation
- The entities managing their private key need to keep it in a secure area such as a Secure Element (SE) and a Hardware Security Module (HSM).

## Privacy Considerations

- The blockchain and a DID document do not contain personally identifiable information (PII).
- Only Verifiable Credentials can contain PII.