# repository_backend/Repository

## Actor Class `Repository`

``` motoko no-repl
class Repository()
```


### Function `getOwners`
``` motoko no-repl
func getOwners() : async [Principal]
```



### Function `getPackageCreators`
``` motoko no-repl
func getPackageCreators() : async [Principal]
```



### Function `setOwners`
``` motoko no-repl
func setOwners(newOwners : [Principal]) : async ()
```



### Function `setPackageCreators`
``` motoko no-repl
func setPackageCreators(newOwners : [Principal]) : async ()
```



### Function `addOwner`
``` motoko no-repl
func addOwner(newOwner : Principal) : async ()
```



### Function `addPackageCreator`
``` motoko no-repl
func addPackageCreator(newCreator : Principal) : async ()
```



### Function `deleteOwner`
``` motoko no-repl
func deleteOwner(oldOwner : Principal) : async ()
```



### Function `deletePackageCreator`
``` motoko no-repl
func deletePackageCreator(oldPackageCreator : Principal) : async ()
```



### Function `init`
``` motoko no-repl
func init() : async ()
```



### Function `getRepositoryName`
``` motoko no-repl
func getRepositoryName() : async Text
```



### Function `getRepositoryInfoURL`
``` motoko no-repl
func getRepositoryInfoURL() : async Text
```



### Function `getReleases`
``` motoko no-repl
func getReleases() : async [(Text, ?Text)]
```



### Function `setRepositoryName`
``` motoko no-repl
func setRepositoryName(value : Text) : async ()
```



### Function `setRepositoryInfoURL`
``` motoko no-repl
func setRepositoryInfoURL(value : Text) : async ()
```



### Function `setReleases`
``` motoko no-repl
func setReleases(value : [(Text, ?Text)]) : async ()
```



### Function `uploadWasm`
``` motoko no-repl
func uploadWasm(wasm : Blob) : async { id : Blob }
```



### Function `uploadModule`
``` motoko no-repl
func uploadModule(module_ : Common.ModuleUpload) : async Common.SharedModule
```



### Function `setDefaultVersions`
``` motoko no-repl
func setDefaultVersions()
```



### Function `getDefaultVersions`
``` motoko no-repl
func getDefaultVersions() : async RepositoryVersions
```



### Function `getWasmModule`
``` motoko no-repl
func getWasmModule(key : Blob) : async Blob
```



### Function `getFullPackageInfo`
``` motoko no-repl
func getFullPackageInfo(name : Common.PackageName) : async Common.SharedFullPackageInfo
```



### Function `setFullPackageInfo`
``` motoko no-repl
func setFullPackageInfo(name : Common.PackageName, info : Common.SharedFullPackageInfo) : async ()
```

TODO@P3: Put a barrier to make the update atomic.
TODO@P3: Don't call it directly.


### Function `getPackage`
``` motoko no-repl
func getPackage(name : Common.PackageName, version : Common.Version) : async Common.SharedPackageInfo
```

