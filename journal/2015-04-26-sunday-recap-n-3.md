---
title: Sunday recap №3
lead: What happened during the last week
author: Sophrinix
date: Apr 26, 2015
---

Welcome to the third post of a series devoted to summarize the
[discussions][discuss] that happened in the last week.

[discuss]: https://github.com/TiForward/discuss/issues

- - -

### iOS Project Layout

- [`#14` iOS Project Layout][issue-14]

Matt Apperson proposed a new project layout for iOS. He proposed two approaches:

Approach number 1:

HAL gets compiled and releases are hosted somewhere. No need to keep compiling this over and over
Titanium SDK gets its own Xcode project. In here is where we will dynamically add native and hyperloop modules when building the app.
The app gets its own Xcode project. This will contain 2 generated files... the inlined JS code, and a .bundle for all assets and such. Other then that the Apps Xcode project would be un-touched by the CLI/Build tools (by default, we would later have a compatibility / easy mode that acts more like current Ti)
With the above considered, we no longer have a build folder, just platform directories.
This approach has one drawback, but it might be a big one:

Many settings and configs we do from a single TiApp.xml would now need to be done per-platform.
This approach has a few benefits to it:

Day 1 new feature support for new platform abilities! It will be easier to work with new features when they are added to the platform. Things like when new entitlements are available... the build tools will no longer cause overwrites that break these things.
You will be able to use native code if/when you want to without having to switch to module dev mode and back to app dev mode. Just add native code to your project. ReactNative allows for this and it is great to not have to switch mindsets mid-project. If you later wanted to make a module from your code you still can.
Fewer things to break in core / core build tools.
We can get things out the door faster this way :)
Approach number 2 (How Ti works now):

HAL gets compiled and releases are hosted somewhere. No need to keep compiling this over and over
Titanium SDK and the app share an xcode project In here is where we will dynamically add native and hyperloop modules when building the app. It will contain the generated files... the inlined JS code, and a .bundle for all assets and such.
This approach has a few drawbacks:

Still need a build directory
Same issues we have every once in a while now with things like entitlements, they are easy to fix but annoying
No ability to drop down to native without switching to building a module (unless maybe we add a place for arbitrary obj-c / swift files but this seems messy and might make debugging hard)
But it also has a few pros:

Out of the box, settings and configs are more cross platform
Compiling might be slightly faster this way, but hard to tell at the moment
One final note: Approach 2 can be built on top of 1 as a plugin.

Going with plan 1 means we have an advanced mode to drop down to when needed, but does not rule out being able to do everything plan 2 can do.

Did I forget something? Disagree with the approach? all ears here :)


There was minimal feedback. 


- - -

### Layout Engine
- [`#6` Layout Engine][issue-6]

Five days ago Matt updated this topic with:
For reference, sake. This project exists -> https://github.com/yomybaby/VirtualTiExample
A "virtual dom" for Ti native UI

Yuchi brought up:
@yomybaby keep me in the morning loop cause I'm digging into ES6 and JSX transformations, please.



- - -

### Backwards compatibility 
- [`#6` Backwards compatibility][issue-12]

Not a lot changed with this conversation, other than further agreement that backwards compatibility should not slow down ti.next


- - -

### Roadmap (aka "the first and most important thing to do" or "focus") 
- [`#6` Backwards compatibility][issue-12]

This topic saw a lot of debate

Chris Barber argued for a CI server for JavaScript Core. https://github.com/TiForward/discuss/issues/13#issuecomment-94582498

Yuchi's comment is worth reading in full https://github.com/TiForward/discuss/issues/13#issuecomment-94592668:
I’ll try to answer @rborn from an higher level.

The challenge we have at hand is not specifically on the engineering side. What we’re trying to achieve here is a broader insight in the topics that need to be discussed for the future of the SDK as a whole. Most of those topics, while seemingly unrelated, are actually very tightly tied.

Take ES6 for example, as @cb1kenobi expressed here and in the related discussion (#8), any decision on this side has important fallbacks on how we’re going to integrate the runtime and how we’re going to build the (new?) pipeline.

Or take the layouting. This is fantastic engineering challenge because it gives us a deeper vision in which kind of UI patterns we’re going to dive in.

What about tooling? The success of a development platform comes from the constellation of tools that comes around it, without those a platform has value only for itself.

Packages and dependencies? Just look at the power npm has over the Node.js/iojs community.

Having access to the native APIs can be considered from an engineering standing point almost a solved issue. We have a new bridge, we have working prototypes of an automatic bindings generator (the ‘metabase’), we have other products that cloned our initial approach and looking good.
What we feel now is that the solution is currently an half-assed one, and probably not the one that we actually need.

Building it all together will bring a shared knowledge and a wider understanding.

Back to the root of the discussion, a real roadmap will emerge in the next weeks, as we solve the smaller technical stoppers and we can start to flesh things out.

rborn cautioned TiForward to not be too ambitious. Again worth reading in full: https://github.com/TiForward/discuss/issues/13#issuecomment-94745326

Infosia pushed a build script and cmake file to build HAL on iOS https://github.com/TiForward/discuss/issues/13#issuecomment-95396357


- - -

### Colophon

A great week. I look *forward* the *next* one.


[issue-6]: https://github.com/TiForward/discuss/issues/6
[issue-12]: https://github.com/TiForward/discuss/issues/12
[issue-13]: https://github.com/TiForward/discuss/issues/13
[issue-14]: https://github.com/TiForward/discuss/issues/14



