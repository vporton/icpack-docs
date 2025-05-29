# package_manager_backend/package_manager
TODO@P3: Methods to query for all installed packages.

## Actor Class `PackageManager`

``` motoko no-repl
class PackageManager({ packageManager : Principal; mainIndirect : Principal; simpleIndirect : Principal; battery : Principal; user : Principal; installationId : Common.InstallationId; userArg : Blob })
```


### Type `HalfInstalledPackageInfo`
``` motoko no-repl
type HalfInstalledPackageInfo = { package : Common.PackageInfo; packageRepoCanister : Principal; modulesInstalledByDefault : HashMap.HashMap<Text, Principal>; minInstallationId : Nat; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob }; bootstrapping : Bool; var remainingModules : Nat; arg : Blob; initArg : ?Blob }
```



### Type `SharedHalfInstalledPackageInfo`
``` motoko no-repl
type SharedHalfInstalledPackageInfo = { package : Common.SharedPackageInfo; packageRepoCanister : Principal; modulesInstalledByDefault : [(Text, Principal)]; minInstallationId : Nat; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob }; bootstrapping : Bool; remainingModules : Nat; arg : Blob; initArg : ?Blob }
```



### Type `HalfUninstalledPackageInfo`
``` motoko no-repl
type HalfUninstalledPackageInfo = { installationId : Common.InstallationId; package : Common.PackageInfo; var remainingModules : Nat }
```



### Type `SharedHalfUninstalledPackageInfo`
``` motoko no-repl
type SharedHalfUninstalledPackageInfo = { installationId : Common.InstallationId; package : Common.SharedPackageInfo; remainingModules : Nat }
```



### Type `HalfUpgradedPackageInfo`
``` motoko no-repl
type HalfUpgradedPackageInfo = { installationId : Common.InstallationId; package : Common.PackageInfo; newRepo : Principal; modulesInstalledByDefault : HashMap.HashMap<Text, Principal>; modulesToDelete : [(Text, Principal)]; var remainingModules : Nat; arg : Blob; initArg : ?Blob }
```



### Type `SharedHalfUpgradedPackageInfo`
``` motoko no-repl
type SharedHalfUpgradedPackageInfo = { installationId : Common.InstallationId; package : Common.SharedPackageInfo; newRepo : Principal; modulesInstalledByDefault : [(Text, Principal)]; modulesToDelete : [(Text, Principal)]; remainingModules : Nat; arg : Blob; initArg : ?Blob }
```



### Function `init`
``` motoko no-repl
func init({  }) : async ()
```



### Function `setOwners`
``` motoko no-repl
func setOwners(newOwners : [Principal]) : async ()
```



### Function `addOwner`
``` motoko no-repl
func addOwner(newOwner : Principal) : async ()
```



### Function `removeOwner`
``` motoko no-repl
func removeOwner(oldOwner : Principal) : async ()
```



### Function `getOwners`
``` motoko no-repl
func getOwners() : async [Principal]
```



### Function `isAllInitialized`
``` motoko no-repl
func isAllInitialized() : async ()
```



### Function `setMainIndirect`
``` motoko no-repl
func setMainIndirect(main_indirect_v : MainIndirect.MainIndirect) : async ()
```



### Function `installPackages`
``` motoko no-repl
func installPackages({ packages : [{ packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO; arg : Blob; initArg : ?Blob }]; user : Principal; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob } }) : async { minInstallationId : Common.InstallationId }
```



### Function `uninstallPackages`
``` motoko no-repl
func uninstallPackages({ packages : [Common.InstallationId]; user : Principal }) : async { minUninstallationId : Common.UninstallationId }
```



### Function `upgradePackages`
``` motoko no-repl
func upgradePackages({ packages : [{ installationId : Common.InstallationId; packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO; arg : Blob; initArg : ?Blob }]; user : Principal; afterUpgradeCallback : ?{ canister : Principal; name : Text; data : Blob } }) : async { minUpgradeId : Common.UpgradeId }
```

We first add new and upgrade existing modules (including executing hooks)
and only then delete modules to be deleted. That's because deleted modules may contain
important data that needs to be imported. Also having deleting modules at the end
does not prevent the package to start fully function before this.


### Function `upgradeStart`
``` motoko no-repl
func upgradeStart({ minUpgradeId : Common.UpgradeId; user : Principal; packages : [{ installationId : Common.InstallationId; package : Common.SharedPackageInfo; repo : Common.RepositoryRO; arg : Blob; initArg : ?Blob }]; afterUpgradeCallback : ?{ canister : Principal; name : Text; data : Blob } }) : async ()
```

Internal.


### Function `onUpgradeOrInstallModule`
``` motoko no-repl
func onUpgradeOrInstallModule({ upgradeId : Common.UpgradeId; moduleName : Text; canister_id : Principal; afterUpgradeCallback : ?{ canister : Principal; name : Text; data : Blob } }) : async ()
```

Internal


### Function `onDeleteCanister`
``` motoko no-repl
func onDeleteCanister({ uninstallationId : Common.UninstallationId }) : async ()
```

Internal


### Function `facilitateBootstrap`
``` motoko no-repl
func facilitateBootstrap({ packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO; arg : Blob; initArg : ?Blob; user : Principal; mainIndirect : Principal; preinstalledModules : [(Text, Principal)] }) : async { minInstallationId : Common.InstallationId }
```

Internal used for bootstrapping.


### Function `installStart`
``` motoko no-repl
func installStart({ minInstallationId : Common.InstallationId; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob }; user : Principal; packages : [{ package : Common.SharedPackageInfo; repo : Common.RepositoryRO; preinstalledModules : [(Text, Principal)]; arg : Blob; initArg : ?Blob }]; bootstrapping : Bool })
```

Internal.

Initialize installation process object.


### Function `onInstallCode`
``` motoko no-repl
func onInstallCode({ installationId : Common.InstallationId; canister : Principal; moduleNumber : Nat; moduleName : ?Text; user : Principal; module_ : Common.SharedModule; packageManager : Principal; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob } }) : async ()
```

Internal


### Function `getAllCanisters`
``` motoko no-repl
func getAllCanisters() : async [({ packageName : Text; guid : Blob }, [(Text, Principal)])]
```

Returns all (default installed and additional) modules canisters.
Internal.


### Function `getInstalledPackage`
``` motoko no-repl
func getInstalledPackage(id : Common.InstallationId) : async Common.SharedInstalledPackageInfo
```



### Function `getModulePrincipal`
``` motoko no-repl
func getModulePrincipal(installationId : Common.InstallationId, moduleName : Text) : async Principal
```

Note that it applies only to default installed modules and fails for additional modules.


### Function `getInstalledPackagesInfoByName`
``` motoko no-repl
func getInstalledPackagesInfoByName(name : Text, guid : Blob) : async { all : [Common.SharedInstalledPackageInfo]; default : Common.InstallationId }
```



### Function `getAllInstalledPackages`
``` motoko no-repl
func getAllInstalledPackages() : async [(Common.InstallationId, Common.SharedInstalledPackageInfo)]
```



### Function `getHalfInstalledPackages`
``` motoko no-repl
func getHalfInstalledPackages() : async [{ installationId : Common.InstallationId; package : Common.SharedPackageInfo }]
```

Internal.


### Function `getHalfUninstalledPackages`
``` motoko no-repl
func getHalfUninstalledPackages() : async [{ uninstallationId : Common.UninstallationId; package : Common.SharedPackageInfo }]
```

Internal.


### Function `getHalfUpgradedPackages`
``` motoko no-repl
func getHalfUpgradedPackages() : async [{ upgradeId : Common.UpgradeId; package : Common.SharedPackageInfo }]
```

Internal.


### Function `getHalfInstalledPackageModulesById`
``` motoko no-repl
func getHalfInstalledPackageModulesById(installationId : Common.InstallationId) : async [(Text, Principal)]
```

TODO@P3: very unstable API.


### Function `setPinned`
``` motoko no-repl
func setPinned(installationId : Common.InstallationId, pinned : Bool) : async ()
```



### Function `removeStalled`
``` motoko no-repl
func removeStalled({ install : [Common.InstallationId]; uninstall : [Common.UninstallationId]; upgrade : [Common.UpgradeId] }) : async ()
```



### Function `userAccountText`
``` motoko no-repl
func userAccountText() : async Principal
```



### Function `userBalance`
``` motoko no-repl
func userBalance() : async Nat
```



### Function `getNewCanisterCycles`
``` motoko no-repl
func getNewCanisterCycles() : async Nat
```

The total cycles amount, including canister creation fee.


### Function `addRepository`
``` motoko no-repl
func addRepository(canister : Principal, name : Text) : async ()
```



### Function `removeRepository`
``` motoko no-repl
func removeRepository(canister : Principal) : async ()
```



### Function `getRepositories`
``` motoko no-repl
func getRepositories() : async [{ canister : Principal; name : Text }]
```



### Function `setDefaultInstalledPackage`
``` motoko no-repl
func setDefaultInstalledPackage(name : Common.PackageName, guid : Blob, installationId : Common.InstallationId) : async ()
```



### Function `withdrawCycles`
``` motoko no-repl
func withdrawCycles(amount : Nat, payee : Principal) : async ()
```



### Function `startModularUpgrade`
``` motoko no-repl
func startModularUpgrade({ installationId : Common.InstallationId; packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO; arg : Blob; initArg : ?Blob; user : Principal }) : async { upgradeId : Common.UpgradeId; totalModules : Nat; modulesToUpgrade : [Text]; modulesToDelete : [(Text, Principal)] }
```

New API for step-by-step upgrades
Initiates an upgrade process and returns upgrade information


### Function `upgradeModule`
``` motoko no-repl
func upgradeModule({ upgradeId : Common.UpgradeId; moduleName : Text; user : Principal }) : async { completed : Bool }
```

Upgrade a specific module as part of modular upgrade


### Function `getModularUpgradeStatus`
``` motoko no-repl
func getModularUpgradeStatus(upgradeId : Common.UpgradeId) : async { upgradeId : Common.UpgradeId; installationId : Common.InstallationId; packageName : Text; completedModules : Nat; totalModules : Nat; remainingModules : Nat; isCompleted : Bool }
```

Get the current status of a modular upgrade


### Function `completeModularUpgrade`
``` motoko no-repl
func completeModularUpgrade(upgradeId : Common.UpgradeId) : async ()
```

Mark all modules as upgraded for a modular upgrade (used for frontend-driven upgrades)
