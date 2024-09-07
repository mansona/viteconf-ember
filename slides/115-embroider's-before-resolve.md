# Embroider's Before Resolve

```js
private async beforeResolve(request) {
  request = await this.handleGlobalsCompat(request);
  request = this.handleImplicitModules(request);
  request = this.handleImplicitTestScripts(request);
  request = this.handleVendorStyles(request);
  request = this.handleTestSupportStyles(request);
  request = this.handleEntrypoint(request);
  request = this.handleRouteEntrypoint(request);
  request = this.handleRenaming(request);
  request = this.handleVendor(request);
  request = this.preHandleExternal(request);

  // this should probably stay the last step in beforeResolve, because it can
  // rehome requests to their un-rewritten locations, and for the most part we
  // want to be dealing with the rewritten packages.
  request = this.handleRewrittenPackages(request);
  return request;
}
```

Note:

Again we're zipping through this code so if anyone is curious and wants to know more about it they can always reach out to me and I'd be happy to walk them through the code in more detail. This single file is 1500 lines long and every line is pretty dense so there is a lot to cover.

The key takeaway of what we're looking at here is that the request is being passed to each fo these functions and every one of them has a chance to alter the request in some way

Time to go deeper