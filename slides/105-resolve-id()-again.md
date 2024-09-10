# resolveId() again

```js
async resolveId(source, importer, options) {
  let request = RollupModuleRequest.from(
    this, source, importer, options.custom);
  
  let resolution = await resolverLoader.resolver.resolve(request);
  switch (resolution.type) {
    case 'found':
    case 'ignored':
      return resolution.result;
    case 'not_found':
      return null;
  }
},
```

Note:

We've loaded the metadata our Embroider resolver using this resolverLoader and we pass a request into the resolve function so let's take a look