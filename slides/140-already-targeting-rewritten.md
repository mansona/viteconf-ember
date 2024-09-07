# Targeting Rewritten

```js
private handleRewrittenPackages(request) {
  let requestingPkg, packageName, targetPkg; // see previous slides

  let originalRequestingPkg = this.packageCache.original(requestingPkg);
  let originalTargetPkg = targetPkg ? this.packageCache.original(targetPkg) : undefined;

  if (targetPkg && originalTargetPkg !== targetPkg) {
    // in this case it doesn't matter whether or not the requesting package
    // was moved. RewrittenPackageCache.resolve already took care of finding
    // the right target, and we redirect the request so it will look inside
    // that target.
    return logTransition(
      'request targets a moved package',
      request,
      this.resolveWithinMovedPackage(request, targetPkg)
    );
  }

  ...
}
```

Note:

Let's write some notes!