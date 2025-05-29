# install

## Function `myCreateCanister`
``` motoko no-repl
func myCreateCanister({ controllers : ?[Principal]; subnet_selection : ?cmc.SubnetSelection; cycles : Nat }) : async* { canister_id : Principal }
```

`cyclesAmount` is the total cycles amount, including canister creation fee.

## Function `myInstallCode`
``` motoko no-repl
func myInstallCode({ installationId : Common.InstallationId; upgradeId : ?Common.UpgradeId; canister_id : Principal; wasmModule : Common.Module; arg : Blob; packageManager : Principal; mainIndirect : Principal; simpleIndirect : Principal; battery : Principal; user : Principal }) : async* ()
```


## Function `copyAssetsIfAny`
``` motoko no-repl
func copyAssetsIfAny({ wasmModule : Common.Module; canister_id : Principal; simpleIndirect : Principal; mainIndirect : Principal; user : Principal }) : async* ()
```


## Type `Callbacks`
``` motoko no-repl
type Callbacks = actor { onCreateCanister : shared ({ installationId : Common.InstallationId; moduleNumber : Nat; moduleName : ?Text; canister : Principal; user : Principal }) -> async (); onInstallCode : shared ({ installationId : Common.InstallationId; canister : Principal; moduleNumber : Nat; moduleName : ?Text; user : Principal; module_ : Common.SharedModule; packageManager : Principal; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob } }) -> async () }
```


## Function `_installModuleCode`
``` motoko no-repl
func _installModuleCode({ moduleNumber : Nat; moduleName : ?Text; installationId : Common.InstallationId; upgradeId : ?Common.UpgradeId; wasmModule : Common.Module; packageManager : Principal; mainIndirect : Principal; simpleIndirect : Principal; battery : Principal; arg : Blob; user : Principal; controllers : ?[Principal]; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob } }) : async* Principal
```


## Function `_installModuleCodeOnly`
``` motoko no-repl
func _installModuleCodeOnly({ moduleNumber : Nat; moduleName : ?Text; installationId : Common.InstallationId; upgradeId : ?Common.UpgradeId; wasmModule : Common.Module; packageManager : Principal; mainIndirect : Principal; battery : Principal; simpleIndirect : Principal; arg : Blob; user : Principal; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob }; canister_id : Principal }) : async* Principal
```

