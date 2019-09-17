---
title: Choosing a graphics pipeline in Unity 2019.3
author: johan
---

Unity has released a lot of news lately about new graphics pipelines in Unity, and it isn't always obvious which one you should choose. While Unity likes to brag about the benefits of each pipeline, they don't really do a good job about explaining the limitations.

Right now, there are three options:

- The old stack
- The high definition render pipeline/HDRP
- The universal render pipeline (formerly lightweight render pipeline/LWRP)

So which one should you use?

## The old stack

It's been there for a while, lots of tutorials. I don't really know too much about it's limitations. But Unity recently indicated that they are moving away from it in favor of the new render pipelines.

It also lacks a lot of the fancy new stuff, such as shader graph etc.

## HDRP

Sounds like the right thing to use if you're developing games to be played on  a computer, right?

It doesn't seem to work with WebGL, however, and  this is really unfortunate. I really enjoy making games for game jams and having a WebGL build is crucial in order to get people to actually play your game.

## Universal render pipeline

In Unity's own words, it "runs everywhere Unity runs", which is great. It means it works with WebGL, and it means it works on mobile, which is really great for porting.

Also, while it used to be called LWRP, it seems to have a lot of advanced features, including shader graph support, reflection probes, post-processing effects and more.

I'm going to stick to this one for now.

EDIT: Actually, after writing this, I found a [comparison table in the official
documentation](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@7.0/manual/universalrp-builtin-feature-comparison.html),
which answers a lot of questions whether you'd want to use
the old pipeline or the universal.
