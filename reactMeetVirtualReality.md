# React, Meet Virtual Reality

Why are we using big game engines for all VR projects?

We could make script that is safe to pass around via just URLs to share VR.
This is how VRScript was released with:
- Easy multiplayer support
- Great state emanagement
- Performance and solid API

Let's grow a VR environment for JS!
- Should target mobile VR
- Start with some basic primitives and build up from there
- Goal is the same as VRScript: Environments can be loaded locally and remotely

Why is VR hard?
- Latency vs Sickness
- 60 frames per second minimum ON MOBILE (90fps on desktop, 120fps on Playstation 4)
- Each eye sees a different view, meaning you have to render twice

So let's get started on handling this challenge:
1. Found bgfx, a cross-platform rending library
  - Was writing a lot of custom windowing code
  - Unclear how node bindings would work on mobile
2. Stumbled on the Oculus Mobile SDK...this works, but still missing javascript
3. Used Spidermonkey to actually plug this up with javascript

Two big issues:
- Garbage being created 120 times per second
- Context switching

The real conclusion:
Just use A-Frame or a game engine like Unity.