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

### Roadmap (Order of importance)



- - -

### Accessing the platform SDK native APIs


- - -

### Ti.Forward Developer Day

- - -

### Backwards compatibility

- - -

### Colophon

A great week. I look *forward* the *next* one.

[issue-1]: https://github.com/TiForward/discuss/issues/1
[issue-2]: https://github.com/TiForward/discuss/issues/2
[issue-3]: https://github.com/TiForward/discuss/issues/3
[issue-4]: https://github.com/TiForward/discuss/issues/4
[issue-5]: https://github.com/TiForward/discuss/issues/5
[issue-6]: https://github.com/TiForward/discuss/issues/6
[issue-7]: https://github.com/TiForward/discuss/issues/7
[issue-8]: https://github.com/TiForward/discuss/issues/8
[issue-9]: https://github.com/TiForward/discuss/issues/9
[issue-11]: https://github.com/TiForward/discuss/issues/11
[issue-12]: https://github.com/TiForward/discuss/issues/12
[issue-13]: https://github.com/TiForward/discuss/issues/13


