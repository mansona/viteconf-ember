
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

Let's write some notes!