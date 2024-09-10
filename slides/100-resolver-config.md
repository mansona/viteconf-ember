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

<sup>*</sup>18 of the 400 lines in this file from a basic boilerplate app 🙈
<!-- .element style="font-size: 70%" -->

Note:

I'm going to skip over all these examples very fast but do you see at the bottom there in the active addons array there is a package that has a root entry in a `.embroider/rewritten-packages` folder

This is the example I want to try to bottom out with you with the 1 minute I have left on the clock.

Going back to our code example of the resolve id