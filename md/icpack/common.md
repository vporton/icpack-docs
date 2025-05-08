# common

## Function `intHash`
``` motoko no-repl
func intHash(value : Int) : Hash.Hash
```


## Type `PackageName`
``` motoko no-repl
type PackageName = Text
```


## Type `Version`
``` motoko no-repl
type Version = Text
```


## Type `VersionRange`
``` motoko no-repl
type VersionRange = (Version, Version)
```


## Type `CommonPackageInfo`
``` motoko no-repl
type CommonPackageInfo = { guid : Blob; name : PackageName; version : Version; shortDescription : Text; longDescription : Text }
```

Common properties of package and virtual package.

## Function `amendedGUID`
``` motoko no-repl
func amendedGUID(guid : Blob, name : PackageName) : Blob
```


## Type `Location`
``` motoko no-repl
type Location = (canister : Principal, id : Blob)
```


## Type `ModuleEvent`
``` motoko no-repl
type ModuleEvent = {#CodeInstalledForAllCanisters; #CodeUpgradedForAllCanisters; #WithdrawCycles}
```


## Type `MethodName`
``` motoko no-repl
type MethodName = { method : Text }
```

Shared/query method name.

## Type `ModuleCode`
``` motoko no-repl
type ModuleCode = {#Wasm : Location; #Assets : { wasm : Location; assets : Principal }}
```


## Type `SharedModule`
``` motoko no-repl
type SharedModule = { code : ModuleCode; installByDefault : Bool; forceReinstall : Bool; canisterVersion : ?Nat64; callbacks : [(ModuleEvent, MethodName)] }
```


## Type `Module`
``` motoko no-repl
type Module = { code : ModuleCode; installByDefault : Bool; forceReinstall : Bool; canisterVersion : ?Nat64; callbacks : HashMap.HashMap<ModuleEvent, MethodName> }
```


## Function `shareModule`
``` motoko no-repl
func shareModule(m : Module) : SharedModule
```


## Function `unshareModule`
``` motoko no-repl
func unshareModule(m : SharedModule) : Module
```


## Type `ModuleUploadCode`
``` motoko no-repl
type ModuleUploadCode = {#Wasm : Blob; #Assets : { wasm : Blob; assets : Principal }}
```


## Type `ModuleUpload`
``` motoko no-repl
type ModuleUpload = { code : ModuleUploadCode; installByDefault : Bool; forceReinstall : Bool; canisterVersion : ?Nat64; callbacks : [(ModuleEvent, MethodName)] }
```


## Type `CheckInitializedCallback`
``` motoko no-repl
type CheckInitializedCallback = { moduleName : Text; how : {#methodName : Text; #urlPath : Text} }
```


## Type `SharedRealPackageInfo`
``` motoko no-repl
type SharedRealPackageInfo = { modules : [(Text, SharedModule)]; dependencies : [(PackageName, [VersionRange])]; suggests : [(PackageName, [VersionRange])]; recommends : [(PackageName, [VersionRange])]; functions : [(PackageName, [VersionRange])]; permissions : [(Text, [MethodName])]; checkInitializedCallback : ?CheckInitializedCallback; frontendModule : ?Text }
```


## Type `RealPackageInfo`
``` motoko no-repl
type RealPackageInfo = { modules : HashMap.HashMap<Text, Module>; dependencies : [(PackageName, [VersionRange])]; suggests : [(PackageName, [VersionRange])]; recommends : [(PackageName, [VersionRange])]; functions : [(PackageName, [VersionRange])]; permissions : [(Text, [MethodName])]; checkInitializedCallback : ?CheckInitializedCallback; frontendModule : ?Text }
```


## Function `shareRealPackageInfo`
``` motoko no-repl
func shareRealPackageInfo(package : RealPackageInfo) : SharedRealPackageInfo
```


## Function `unshareRealPackageInfo`
``` motoko no-repl
func unshareRealPackageInfo(package : SharedRealPackageInfo) : RealPackageInfo
```


## Type `RealPackageInfoUpload`
``` motoko no-repl
type RealPackageInfoUpload = { modules : [(Text, ModuleUpload)]; dependencies : [(PackageName, [VersionRange])]; suggests : [(PackageName, [VersionRange])]; recommends : [(PackageName, [VersionRange])]; functions : [(PackageName, [VersionRange])]; permissions : [(Text, [MethodName])]; checkInitializedCallback : ?CheckInitializedCallback; frontendModule : ?Text }
```


## Type `VirtualPackageInfo`
``` motoko no-repl
type VirtualPackageInfo = { choice : [(PackageName, [VersionRange])]; default : PackageName }
```


## Type `SharedPackageInfo`
``` motoko no-repl
type SharedPackageInfo = { base : CommonPackageInfo; specific : {#real : SharedRealPackageInfo; #virtual : VirtualPackageInfo} }
```


## Type `PackageInfo`
``` motoko no-repl
type PackageInfo = { base : CommonPackageInfo; specific : {#real : RealPackageInfo; #virtual : VirtualPackageInfo} }
```


## Function `sharePackageInfo`
``` motoko no-repl
func sharePackageInfo(info : PackageInfo) : SharedPackageInfo
```


## Function `unsharePackageInfo`
``` motoko no-repl
func unsharePackageInfo(info : SharedPackageInfo) : PackageInfo
```


## Type `InstallationId`
``` motoko no-repl
type InstallationId = Nat
```


## Type `UninstallationId`
``` motoko no-repl
type UninstallationId = Nat
```


## Type `UpgradeId`
``` motoko no-repl
type UpgradeId = Nat
```


## Type `RepositoryRO`
``` motoko no-repl
type RepositoryRO = actor { getRepositoryName : shared query () -> async Text; getRepositoryInfoURL : shared query () -> async Text; getReleases : shared query () -> async [(Text, ?Text)]; getPackage : shared query (name : PackageName, version : Version) -> async SharedPackageInfo; getWasmModule : shared query (sk : Blob) -> async Blob }
```


## Type `InstalledPackageInfo`
``` motoko no-repl
type InstalledPackageInfo = { id : InstallationId; var package : PackageInfo; var packageRepoCanister : Principal; var modulesInstalledByDefault : HashMap.HashMap<Text, Principal>; additionalModules : HashMap.HashMap<Text, Buffer.Buffer<Principal>>; var pinned : Bool }
```


## Function `modulesIterator`
``` motoko no-repl
func modulesIterator(pkg : InstalledPackageInfo) : Iter.Iter<(Text, Principal)>
```

Iterate over all modules in `pkg.namedModules`.

## Function `numberOfModules`
``` motoko no-repl
func numberOfModules(pkg : InstalledPackageInfo) : Nat
```


## Type `SharedInstalledPackageInfo`
``` motoko no-repl
type SharedInstalledPackageInfo = { id : InstallationId; package : SharedPackageInfo; packageRepoCanister : Principal; modulesInstalledByDefault : [(Text, Principal)]; additionalModules : [(Text, [Principal])]; pinned : Bool }
```


## Function `installedPackageInfoShare`
``` motoko no-repl
func installedPackageInfoShare(info : InstalledPackageInfo) : SharedInstalledPackageInfo
```


## Function `installedPackageInfoUnshare`
``` motoko no-repl
func installedPackageInfoUnshare(info : SharedInstalledPackageInfo) : InstalledPackageInfo
```


## Type `SharedFullPackageInfo`
``` motoko no-repl
type SharedFullPackageInfo = { packages : [(Version, SharedPackageInfo)]; versionsMap : [(Version, Version)] }
```


## Type `FullPackageInfo`
``` motoko no-repl
type FullPackageInfo = { packages : HashMap.HashMap<Version, PackageInfo>; versionsMap : HashMap.HashMap<Version, Version> }
```


## Function `shareFullPackageInfo`
``` motoko no-repl
func shareFullPackageInfo(info : FullPackageInfo) : SharedFullPackageInfo
```


## Function `unshareFullPackageInfo`
``` motoko no-repl
func unshareFullPackageInfo(info : SharedFullPackageInfo) : FullPackageInfo
```


## Function `extractModuleLocation`
``` motoko no-repl
func extractModuleLocation(code : ModuleCode) : (Principal, Blob)
```


## Function `extractModuleUploadBlob`
``` motoko no-repl
func extractModuleUploadBlob(code : ModuleUploadCode) : Blob
```


## Type `CanisterFulfillment`
``` motoko no-repl
type CanisterFulfillment = { threshold : Nat; topupAmount : Nat }
```


## Function `principalToSubaccount`
``` motoko no-repl
func principalToSubaccount(principal : Principal) : Blob
```


## Value `cycles_transfer_fee`
``` motoko no-repl
let cycles_transfer_fee
```

