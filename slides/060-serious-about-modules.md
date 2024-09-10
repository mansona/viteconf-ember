# Serious about Modules!

<div>

![eval define](/eval-define.png) <!-- .element style="width: 1300px;" -->

🤢

</div>

<!-- .element class="fragment" -->

Note:

The second issue that we had was that Vite takes ES modules seriously. Sure we were pioneers in the use of modules in ember but that was mostly just authoring format. ember-cli rebuilt everything into AMD modules under the hood 

🙈

not great, but what is worse is that even with Embroider and Webpack doing its magic... it all boiled down to a horrible AMD with webpack eval monstrocity in the build output. 

SLIDE

I know you can't see it in this screenshot but there is a bunch of AMD requires and defines in that eval script too... not great

If we were serious about Vite we needed to get serious about modules and clean up our act.

Now we had the bones of a plan but there was a tonne of work still to do, it was going to take a long time for a fully open source community project like Ember if we didn't change the script. 
