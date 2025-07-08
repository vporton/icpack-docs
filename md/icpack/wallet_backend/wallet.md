# wallet_backend/wallet

## Actor Class `Wallet`

``` motoko no-repl
class Wallet({ installationId : Nat; packageManager : Principal })
```


### Function `setOwner`
``` motoko no-repl
func setOwner(signature : Blob) : async ()
```

Change wallet owner after verifying caller's signature with the provided public key.


### Function `getLimitAmounts`
``` motoko no-repl
func getLimitAmounts() : async { amountAddCheckbox : ?Float; amountAddInput : ?Float }
```



### Function `setLimitAmounts`
``` motoko no-repl
func setLimitAmounts(values : { amountAddCheckbox : ?Float; amountAddInput : ?Float }) : async ()
```



### Function `getTokens`
``` motoko no-repl
func getTokens() : async [Token]
```



### Function `addToken`
``` motoko no-repl
func addToken(token : Token) : async ()
```



### Function `removeToken`
``` motoko no-repl
func removeToken(canisterId : Principal) : async ()
```



### Function `addArchiveCanister`
``` motoko no-repl
func addArchiveCanister(symbol : Text, archiveCanisterId : Principal) : async ()
```



### Function `isAnonymous`
``` motoko no-repl
func isAnonymous() : async Bool
```

