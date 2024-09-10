# Pipeline

<div class="card-wrapper">

![pipeline](/pipeline1.png) <!-- .element class="fragment" -->

![pipeline](/pipeline2.png) <!-- .element class="fragment" -->

![pipeline](/pipeline3.png) <!-- .element class="fragment" -->

</div>

Note:

sure it was sophisticated for its time but.. broccoli has a core assumption that your files are represented as a tree (essentially the same way that your operating system looks at them). But the cool thing is that you get a pipeline of trees where any file can be changed, files can be added, removed. It's all really powerful... but I wonder if any of you have seen the issue with a system like this. It doesn't match the modern build system concept of starting at an entrypoint and walking the module graph. With broccoli you have to work on whole trees all the time and you have very little knowledge about which modules are being used so you can't make the build any more efficient and you can't do any code splitting or tree shaking (ironcally - all trees with no shaking 😭).

so how do we marry these two worlds? How do we bring Ember into a world where we need to understand the module graph? 