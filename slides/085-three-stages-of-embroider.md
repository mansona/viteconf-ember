# Three stages of Embroider


<div class="card-wrapper">
<div class="card-thingy">
  
Stage 1

convert all your addons <!-- .element style="text-align: left; width: 90%;" -->

</div>

<div class="card-thingy">

Stage 2 

convert your app <!-- .element style="text-align: left; width: 90%;" -->

</div>

<div class="card-thingy">


Stage 3 

Pass your converted app and addons over to your bundler <!-- .element style="text-align: left; width: 90%;" -->

That's vite 🎉 <!-- .element class="fragment" style="font-size: 60%;" -->

</div>
</div>


Note:

I mentioned that embroider allows you to use all your normal Ember build shenanigans while still upgrading to modern tooling. well that's because we convert all the broccoli nonsense into "real" packages for you in stage 1 and stage 2. If you were thinking of building a system like this that converts something for you you might think "let's emulate the api" 