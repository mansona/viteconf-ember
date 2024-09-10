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

This code might look complicated but it's not all that bad. we can summarise it as

- check if there is anything to do before even trying to resolve
- hand it off to vite/rollup/esbuild to try to resolve
- if we didn't find it then see if there is any ember-specific fallback we need to do

we're trying to follow the example of a rewritten package so using my existing knowledge of where things live I'm going to jump straight into the before Resolve and take a look. 