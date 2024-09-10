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

now we have most of the stuff we need to even start asking the questions we would like to ask. we have info on the package that the request is coming from. we have info about the target package that we're trying to ask about.

Next up we start checking if either the requesting package or the target package have been rewritten. if so we can start doing some slightly magical things with the request and alter the request before it bubbles out to Vite/rollup or esbuild
