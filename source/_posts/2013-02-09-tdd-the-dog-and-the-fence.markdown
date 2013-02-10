---
layout: post
title: "TDD: The Dog And The Fence"
date: 2013-02-09 21:22
comments: true
categories: hack life
---

You thought [Test Driven Development: By Example](http://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530) (Kent Beck) was a biblical ouvrage perfectly illustrating how to apply TDD to your software practice?  Think again! Today, I claim to have a __better example__.

## Say What? 

Since last Saturday, the usual maintainer of `the_house` is gone in vacation.  She's been wandering around in the South of the US, lurking at Florida's beaches.  Before flying out, she asked me to maintain her project and ensure that everything was running smoothly.  There's not much to do, so it's not really a problem.

Or so I thought!

When would be a better time for `the_house` to crash than when its maintainer is away?

<!-- more -->

## The Setting

About two days ago, an area spanning at least the /16 block started to accumulate a lot of garbage (some collocated neighbours call it "snow"), with no clear means to evacuate it. As any decent person would do, I undertook the enterprise of manually moving much of that crap out of main memory and moving it to swap in front of `the_house`, out of the way and leaving room for `cars` and `pedestrians` to execute properly.

### First Sign Of Failure

For a few hours, all was good.  Then two days ago, in the morning, a prescient sign of failure appeared.  The collocated admin of `another_house` sent me an e-mail, which he quite oddly printed and stamped on `the_house.door` (what a strange individual).  Apparently, two of our `dogs` had escaped from within our local network.

Here you might be wondering "what the hell are they doing with two `dogs`".  It happens that the users of `the_house` enjoy the company of `dogs` so they maintain two of them within the boundaries (or so they thought!) of their localhost.  They do so against any common sense, every decent human being knowledgeably avoiding such annoying-ware for fear they will clutter their `house` 
with garbages of all kind, or even destroy parts of `the_house`.

So although it's entirely in their right to put their instance of `the_house` at risk like that, they have to ensure the `dogs` can't make it out to the neighbour systems (and destroy their environment)!

While nothing of that happened on this specific occurrence, still, that morning, two `dogs` crossed the `fence` firewall.

At first, I thought it was a misconfigured setting.  I went about `fence` and discovered a benign leak caused by a parameter.  I fixed it with a simple hack; I found somewhere in `the_house.trash` a piece of scrap that could apparently block the leak.

> Easy-peasy!

...did I think to myself!  

> Those vile `dogs` won't make it out anytime soon! 

Blah!  My lack of humility would take a little more than 12 hours to pay me back with a good dose of failure.

### Error, error, error!

So that initial failure was maybe a little more complicated than a misconfigured dotfile.  As I logged back into `the_house` on that evening, I found the two `dogs` missing.  Apparently, they had yet again fled.  For some insane reason, the closest neighbour of our /24 block decided to take custody of the escaped `dogs` while waiting for the suppleant maintainer of `the house` (that is me) to come back.

Well well well, that was quite odd.  The scrap I had put in front of the leak was gone, and it was nowhere to be found around it (I suspect the two `kids` in the collocated `house` abused their rights on `fence` and purposely freed the scrap away from the leak in order to run their insatiable `play` program onto `dogs`).

Indeed, the problem was bigger than I thought.  There was a need to fix this `fence` or `the_house` could be put in jeopardy in this collocated server, pissing off the co-users of the box.

By now you might think that life is serving me a painful injection of wisdom, right into the brain.  Well you're wrong. 

### My Brain Is Harder Than Steel

The next (this) morning, as I wake up and prepare to go take a shower, I find myself carelessly believing that `dogs` won't find their way through the leak in a mere 15 minutes, while I wash and get them back inside.

And indeed, yet again they fled.  They escaped in all their glory, deciding this time to make an assault of the /16 block neighbours.  With a decent amount of shame, I find myself pinging all corners of the area, trying to find where the `dogs` are.  Luckily, they didn't go _too_ far and 15 minutes later, I've brought them back home.  

I put them to idle behind a virtual network we call `crate` and I leave for the day.  On the way to my destination, I fill in a bug report for `the_house` and mark it as confirmed.

## At Last, Common Sense Prevails

### TL;DR: 
The dogs escaped the house three times before I realized (or accepted) that there was a real problem with the fence.  Also, I put my _TL;DR_ in the middle of the damn text, just as pointless as it can be.  I saw that elsewhere and thought "that's a pretty pointless location where to put a _TL;DR_".  Now, you've been served as well! 

> What a nice guy!

###  The Real Nature of the Beast

It so happens that a massive amount of crap, so called `snow`, has elevated the levels of pressure on `fence`, making it prone to fail upon application of `dogs`' requests to traverse it.  In all usual circumstances, `fence` should have enough resources to hold the `dogs` at bay.  However, that extra `snow` has lowered the barrier of entry for the `dogs` to cross it.  On top of that, there's that annoying blatant hole in `fence` which is not helping.

I really need to fix this bug, once and for all.  How can I do that? Like any fixer will tell you, the first step to take is to define a test case that confirms the presence of the bug.

In our case, what we need is:

* An instance of `dog`, preferably a resourceful, motivated and hyperactive dog. Cast it into an `overexcited_dog`.

{% img /images/picture_of_lovelace.jpg 800 450 'A Resourceful, motivated and hyperactive dog (perhaps a bit evil too)' %}

* An insufficient `fence`, preferably misconfigured (that is, with "holes" in it).

### The Test

What kind of test can we use to highlight the failures of our `fence`?  It's quite simple and it holds in three steps:

1. Take the `overexcited_dog` and set it behind the `fence`.
2. Get on the other side of the `fence` with an array of `meat`.  The `overexcited_dog` must be aware of the presence of `meat` in the array.
3. Shake the array of `meat` until `overexcited_dog` be upcast into a `way_too_excited_dog`.

The test fails if `way_too_excited_dog` gets across the `fence` and eats the array of `meat`.  If the `way_too_excited_dog` doesn't make it through, it will be downcast into a `whining_dog`, which can be recognized by its near-panic state of despair.  It is important that you end the test __immediately__ when the `dog` reaches this state, because it's way too cruel otherwise.  To do so, just give an entry from `meat` to the `dog` and let it back into `the_house`, and everything shall be fine.

## Red, Green, Refactor

We now have a failing test.  Indeed, when I run it, I invariably obtain a `way_too_excited_dog`, which who eats my array of `meat`.

I can't keep this test _red_ for too long (I don't have enough meat!), so I need to find a fix!

### First Try

I go around `the_house` and find a metal shovel.  Maybe if I dig a trench around `fence`, my `overexcited_dog` won't make it through (despite the hole)!

I run the test:

> __Red__.  

Woah! What a pity!

### Second Try

Taking a piece of `fence` covering a side of the wall from `the_house` and cutting it away from the rest, I then proceed to apply it upon the hole in the `fence`, effectively patching it.

I run the test:

> __Red__.  

What?  Again?  Indeed, the `way_too_excited_dog` made it through in some unexpected way: it jumped over the `fence` altogether.

Despite the trench and the patched hole, we still have a red test!  Thanks to TDD, I can now see that the real nature of my bug is not only the hole in the wall, but the raw nature of the `fence`!

Luckily enough, the test I designed above is perfectly adapted to this scenario (since it brought it to our ear loud-and-clear).

I return to my tools and observe the `fence` once again.  The `way_too_excited_dog` managed to cross it by climbing on the bending `fence`.  Given enough `over_excitement`, the `dog` effectively uses the `fence` as a spring to propel itself higher up, jumping to meet the delicious `meat`. I grab a plank of wood from `the_house.basement` and bring it outside to apply it on the lowest side of the `fence`.

By stretching the wire of the chicken fence (oh yeah, I forgot to mention it _is_ a chicken fence, hah!) and fixing it at the plank, and doing the same on the second half of the `fence` with a wooden stick that I find around, I manage to set the `fence` straight.

Then I run my test once again.

### Green!

The `overexcited_dog` quickly transforms into `whining_dog`.  This (chicken) `fence` has overcome its resourcefulness, motivation and hyperactivity!

### Refactor!

Now, this is the state of the `fence`:

{% img /images/weak_chicken_fence.jpg 800 450 'Quite A Weak Fence, Indeed' %}

It's quite a weak fence if you ask me.  Although our test for `the_house.fence` is green, we're left with really ugly hacks around.  We can't let our codebase in this state!

Unfortunately, `fence` is too big an endeavour to undertake until the `Spring` release.  The whole thing will have to be rebuilt from scratch, using an actual, proper `fence` this time.  In the meantime, we'll have to deal with this hack and keep an eye on our test - make sure it stays green! 

