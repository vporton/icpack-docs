# bootstrapper_backend/bookmarks

## Actor Class `Bookmarks`

``` motoko no-repl
class Bookmarks(initialOwner : Principal)
```


### Type `Bookmark`
``` motoko no-repl
type Bookmark = { frontend : Principal; backend : Principal }
```



### Function `init`
``` motoko no-repl
func init(args : { bootstrapper : Principal }) : async ()
```



### Function `getUserBookmarks`
``` motoko no-repl
func getUserBookmarks() : async [Bookmark]
```



### Function `hasBookmark`
``` motoko no-repl
func hasBookmark(b : Bookmark) : async Bool
```



### Function `addBookmark`
``` motoko no-repl
func addBookmark() : async Bool
```

Returns whether bookmark already existed.
