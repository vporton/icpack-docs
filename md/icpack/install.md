# install

## Function `myCreateCanister`
``` motoko no-repl
func myCreateCanister() : async* { canister_id : Principal }
```

`cyclesAmount` is the total cycles amount, including canister creation fee.

## Function `myInstallCode`
``` motoko no-repl
func myInstallCode() : async* ()
```


## Function `copyAssetsIfAny`
``` motoko no-repl
func copyAssetsIfAny() : async* ()
```


## Type `Callbacks`
``` motoko no-repl
type Callbacks = actor { onCreateCanister : shared ({ installationId : Common.InstallationId; moduleNumber : Nat; moduleName : ?Text; canister : Principal; user : Principal }) -> async (); onInstallCode : shared ({ installationId : Common.InstallationId; canister : Principal; moduleNumber : Nat; moduleName : ?Text; user : Principal; module_ : Common.SharedModule; packageManager : Principal; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob } }) -> async () }
```


## Function `_installModuleCode`
``` motoko no-repl
func _installModuleCode() : async* Principal
```


## Function `_installModuleCodeOnly`
``` motoko no-repl
func _installModuleCodeOnly() : async* Principal
```

