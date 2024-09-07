# Resolver Config

```json
{
  "renameModules": {
    "@ember/object/computed.js": "ember-source/@ember/object/computed.js",
  },
  "renamePackages": {
    "live-reload-middleware": "ember-cli-inject-live-reload"
  },
  "engines": [{
    "activeAddons": [{
      "name": "@ember/test-helpers",
      "root": "/tmp/my-fancy-app/node_modules/.embroider/rewritten-packages/@ember/test-helpers.bfec475c/node_modules/@ember/test-helpers",
      "canResolveFromFile": "/tmp/my-fancy-app/package.json"
    }],
  }],
}
```

<sup>*</sup>18 of the 400 lines in this file from a basic app 🙈
<!-- .element class="fragment" style="font-size: 70%" -->

Note:

you can see an example of what I said at the beginning of fake module renaming, it's not actually fake any more but you can see that `@ember/object` actually comes from the ember-source package

then in the engines array, the first engine has an active addon that has a root in rewritten-packages. This is the example I want to try to show you with the 1 minute I have left on the clock.

Going back to our code example of the resolve id