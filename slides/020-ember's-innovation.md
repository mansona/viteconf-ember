# Ember's Innovation

<style>

.card-wrapper {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
}

.card-thingy {
  border-radius: 30px;
  
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
  border: 3px solid black;
}

.card-thingy img {
  /* min-width: 100%; */
  padding: 15px;
  object-fit: cover;
  height: 160px;
  min-height: 160px;
}

</style>

<div class="card-wrapper">
<div class="card-thingy">

<img src="/classes.png" >
  
ES Classes

</div>

<div class="card-thingy">
<img src="/box.svg" >

ES Modules

</div>

<div class="card-thingy">
<img src="/cogs.webp" >

Build Systems

</div>
</div>

Note:

Classes in JavaScript actually happened with Ember's help, Ember Core Team members were working with TC39 at the time they were being added.
ES modules - we were using them as part of our authoring format before they were in the language.
ember-cli, our baked in build system, was so ahead of its time that there were many arguments about if frameworks even needed a build system at the time. And since we're all here at ViteConf, I guess the team build system has won that particular battle!!

but with all those firsts we have a few problems, expeicially when we care so much about stability and not leaving anyone behind. our pree-class "class" object was the basis for all the major building blocks of the framework. We've cleaned up a bunch of them but still not all of them