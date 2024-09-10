# handleRewrittenPackages()

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
  } else if (originalRequestingPkg !== requestingPkg) {
    if (targetPkg) {
      // in this case, the requesting package is moved but its destination is
      // not, so we need to rehome the request back to the original location.
      return logTransition(
        'outbound request from moved package',
        request,
        request
          // setting meta here because if this fails, we want the fallback
          // logic to revert our rehome and continue from the *moved* package.
          .withMeta({ originalFromFile: request.fromFile })
          .rehome(resolve(originalRequestingPkg.root, 'package.json'))
      );
    } else {
      // requesting package was moved and we failed to find its target. We
      // can't let that accidentally succeed in the defaultResolve because we
      // could escape the moved package system.
      return logTransition('missing outbound request from moved package', request, request.notFound());
    }
  }

  return request;
}
```
<!-- .element style="font-size: 18%;" -->

Note:

This is what it looks like in handleRewrittenPackages. It's way too small for a single slide