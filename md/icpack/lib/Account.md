# lib/Account

## Type `Account`
``` motoko no-repl
type Account = { owner : Principal; subaccount : ?Blob }
```


## Type `ParseError`
``` motoko no-repl
type ParseError = {#malformed : Text; #not_canonical; #bad_checksum}
```


## Function `toText`
``` motoko no-repl
func toText() : Text
```

Converts an account to text.

## Function `fromText`
``` motoko no-repl
func fromText(text : Text) : Result.Result<Account, ParseError>
```

Parses account from its textual representation.

## Function `checkSum`
``` motoko no-repl
func checkSum(owner : Principal, subaccount : Blob) : Text
```

