
```js
private handleRewrittenPackages(request) {
  let requestingPkg = this.packageCache.ownerOfFile(request.fromFile);
  if (!requestingPkg) {
    return request;
  }
  let packageName = getPackageName(request.specifier);
  if (!packageName) {
    // relative request
    return request;
  }

  let targetPkg;
  if (packageName !== requestingPkg.name) {
    // non-relative, non-self request, so check if it aims at a rewritten addon
    try {
      targetPkg = this.packageCache.resolve(packageName, requestingPkg);
    } catch (err) {
      if (err.code !== 'MODULE_NOT_FOUND') {
        throw err;
      }
    }
  }
  ...
}
```

Note:

here we access the package cache to see where the reuest is coming from. The package cache is using the same information that we saw in our config file a second ago. If the request is coming from somehwere that we don't know anything about we return the request unchanged

the same is true if the specifier, the acual import path, doesn't have a package name. We essentially assume it's a relative import so we don't do anything and return the request unchanged

next we check to see if we're make a request to a target package that isn't the same as the package we're currently in. Essentially a non-relative, non-self request like it says there in the comment