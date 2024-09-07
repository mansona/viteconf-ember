# Three stages of Embroider

- Stage 1 
  - convert all your addons

- Stage 2 
  - convert your app

- Stage 3 
  - pass your converted app and addons over to your bundler (that's Vite!)

Note:

I mentioned that embroider allows you to use all your normal Ember build shenanigans while still upgrading to modern tooling. well that's because we convert all the broccoli nonsense into "real" packages for you in stage 1 and stage 2. If you were thinking of building a system like this that converts something for you you might think "let's emulate the api" 