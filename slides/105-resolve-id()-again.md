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

Let's write some notes!