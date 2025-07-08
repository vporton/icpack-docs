# lib/UserAuth

## Type `PubKey`
``` motoko no-repl
type PubKey = Blob
```


## Type `PrivKey`
``` motoko no-repl
type PrivKey = Blob
```


## Function `verifySignature`
``` motoko no-repl
func verifySignature(pubKey : PubKey, user : Principal, signature : Blob) : Bool
```

Verify that the signature was produced by the private key corresponding to `pubKey`.
Traps on malformed key or signature.
