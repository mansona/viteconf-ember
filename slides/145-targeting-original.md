
```js
private handleRewrittenPackages(request) {
  let requestingPkg, packageName, targetPkg; // see previous slides
  let originalRequestingPkg, originalTargetPkg; // see previous slides

  if (originalRequestingPkg !== requestingPkg) {
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

Note:

Let's write some notes!