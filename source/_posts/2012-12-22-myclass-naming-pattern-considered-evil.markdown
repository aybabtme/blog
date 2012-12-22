---
layout: post
title: "MyClass Naming Pattern Considered Evil"
date: 2012-12-22 05:31
comments: true
categories: rant code
---

From time to time, I've seen people online or at school having a class
such as:

``` Java
public class Shredder {
    public void shredEverything(){
      // destroyyyyyy
    }
}
```
and rolling out custom implementation using this kind of brain-farted
naming pattern:
``` Java
public class MyShredder extends Shredder {
    @Override
    public void shredEverything(){
      // oh hai, I just want to shred paper, nothing else
    }
}
```

Huuuuuuuurrrrrrr.....

You know what?  JUST NAME YOUR CLASS `PaperShredder` and LET US ALL BE
HAPPIER!

``` Java
public class PaperShredder extends Shredder {
    /** This thing only shreds paper */
}
```

When I eventually come across a stack trace with the `MyImplementation`
name that your brain farted, I'm left to wonder what kind of information you
expect readers to grasp from that particular name.

I understand that you're proud of your code, that you think "Hey guys,
  that's MY class!" and everything, but knowing that this is 
  `YourImplementation` is pretty fucking pointless to everybody.

> Don't name your classes with the `My` prefix!!!

Just don't do it!  If you implement something at random and feel there's
no better name coming to your mind at that time, well... just rename it
anyway!

There's no way on earth that `MyException` will ever mean something
useful to anybody, not even you.  If you don't understand that, please 
hand over your keyboard to your kindergarden instructor.
