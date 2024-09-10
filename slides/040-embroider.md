# Embroider

![foe](/challenger_meme.png)

![embroider](/embroider.png) <!-- .element class="fragment" style="position: absolute; top: 300px; right:280px; transform: rotate(10deg); width: 300px" -->

Note:

Embroider is like a semi-magical glue code that bridges the gap beween the old way of doing things in Ember and the new. It allows you to use all of your existing ember concepts like addons, strange fake modules, automatic file discovery etc but it essentially pre-processes all your ember-cli based broccoli trees and outputs a (semi) prestine app that a bundler like Webpack can look at and do its magic. 

Woo hoo, problem solved let's ship Embroider to everyone! ... not so fast. literally. 

The previous version of Embroider that relied on webpack wasn't all that big of a sell for people. It would work 80% of the time, so most apps could use it, but when it broke it would break in weird and wonderful ways that were very hard to understand. Some of this was because Webpack's errors can be cryptic at the best of times but one of the fundemental issues that we were facing was that we were crowbaring a bundler into an outdated build paragdime of these broccoli trees. Even Webpack wasn't designed to work this way. Back when webpack 5 came out we saw a massive performance drop because the library mode of webpack didn't have all the optimisations that were built into the webpack dev server and we were not using the dev server

We were stuck without a plan until... 