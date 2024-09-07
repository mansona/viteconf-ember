# resolveId()

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
<!-- .element style="font-size: 80%; margin: 0; width: 100%" -->

Note:

at first glance the vite plugin isn't doing all that much. We have this custom resolver that we pass a request to and if it finds a thing great! No big deal. But what is fun is when you look under the hood of that resolver. 

a resolver loader locates a temp folder in your current app where a ember prebuild has output a bunch of metadata files that tells our embroider resolver what to do with a request.

right maybe let's back up a second what is a prebuild even doing? 
