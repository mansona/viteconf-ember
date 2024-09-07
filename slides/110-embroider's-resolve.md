# Embroider's Resolve

```js
async resolve(request) {
  request = await this.beforeResolve(request);
  if (request.resolvedTo) {
    return request.resolvedTo;
  }

  let resolution = await request.defaultResolve();
  switch (resolution.type) {
    case 'found':
      return resolution;
    case 'not_found':
      break;
  }
  let nextRequest = await this.fallbackResolve(request);
  if (nextRequest === request) {
    // no additional fallback is available.
    return resolution;
  }
  // do some other post-fallback stuff
}
```

Note:

This code might look complicated but it's actually vastly simplified (and has had all the types stripped out). This slide could be summarised as 

- check if there is anything to do before even trying to resolve
- hand it off to vite/rollup/esbuild to try to resolve
- if we didn't find it then see if there is any ember-specific fallback we need to do

the code we're looknig for is in beforeResolve so let's jump in there and take a look