# MockCyclesLedger
Mock `CyclesLedger.create_canister` implementation using `IC.create_canister` (for testing).
IT DOES NOT CONFORM TO THE SPECS!
It's useful for testing code using `CyclesLedger.create_canister` on local net.

## Actor Class `MockCyclesLedger`

``` motoko no-repl
class MockCyclesLedger(token_args : ICRC1.TokenInitArgs)
```


### Function `icrc1_name`
``` motoko no-repl
func icrc1_name() : async Text
```

Functions for the ICRC1 token standard


### Function `icrc1_symbol`
``` motoko no-repl
func icrc1_symbol() : async Text
```



### Function `icrc1_decimals`
``` motoko no-repl
func icrc1_decimals() : async Nat8
```



### Function `icrc1_fee`
``` motoko no-repl
func icrc1_fee() : async ICRC1.Balance
```



### Function `icrc1_metadata`
``` motoko no-repl
func icrc1_metadata() : async [ICRC1.MetaDatum]
```



### Function `icrc1_total_supply`
``` motoko no-repl
func icrc1_total_supply() : async ICRC1.Balance
```



### Function `icrc1_minting_account`
``` motoko no-repl
func icrc1_minting_account() : async ?ICRC1.Account
```



### Function `icrc1_balance_of`
``` motoko no-repl
func icrc1_balance_of(args : ICRC1.Account) : async ICRC1.Balance
```



### Function `icrc1_supported_standards`
``` motoko no-repl
func icrc1_supported_standards() : async [ICRC1.SupportedStandard]
```



### Function `icrc1_transfer`
``` motoko no-repl
func icrc1_transfer(args : ICRC1.TransferArgs) : async ICRC1.TransferResult
```



### Function `mint`
``` motoko no-repl
func mint(args : ICRC1.Mint) : async ICRC1.TransferResult
```

In our mock object, anyone can mint.


### Function `burn`
``` motoko no-repl
func burn(args : ICRC1.BurnArgs) : async ICRC1.TransferResult
```



### Function `get_transactions`
``` motoko no-repl
func get_transactions(req : ICRC1.GetTransactionsRequest) : async ICRC1.GetTransactionsResponse
```



### Function `get_transaction`
``` motoko no-repl
func get_transaction(i : ICRC1.TxIndex) : async ?ICRC1.Transaction
```



### Function `deposit_cycles`
``` motoko no-repl
func deposit_cycles() : async ()
```

