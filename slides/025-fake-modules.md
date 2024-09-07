# Fake Modules

```js
// Not a real package 🫠
import Something from '@ember/something';
```
<!-- .element style="font-size: 100%" -->

gets magically converted to

```js
import Something from 'ember-source/something/index';
```
<!-- .element style="font-size: 80%" -->

🔔 FORESHADOWING!! 🔔
<!-- .element class="fragment" -->

Note:

Our module system started out as a fake module system where you could import from `@ember/something` and it would essentially be rewritten during build time to `ember-source/something/index`

but the biggest foundational system that is relevant to the story of vite is ember-cli, and the underlying build technology that drives it: