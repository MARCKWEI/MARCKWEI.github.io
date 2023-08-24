---
layout: archive
title: "PROJECTS"
permalink: /projects/
author_profile: true
---

{% include base_path %}


## UNDERWAY

Recently, I've turned my attention to **WebAssembly**, which I think has a lot of potential and is now supported by all major browsers.

I've implemented a tool to fuzz the WebAssembly compiler of browsers, based on an idea presented at [Black Hat Asia 2023](https://www.blackhat.com/asia-23/briefings/schedule/#attacking-the-webassembly-compiler-of-webkit-30926). 
My tool has found 6 and 2 WebAssembly-related bugs in JavaScriptCore and SpiderMonkey, respectively.

However, I'm not familiar with the WebAssembly vulnerability exploit, and I don't know how to do anything with them yet. If you are interested in exploiting webassembly vulnerabilities, please feel free to communicate with me.

## FINISHED

[PatchFuzz](https://github.com/marckwei/patchFuzz): I am the major contributor to this project, and the code will be available to the public after the paper has been accepted.

[FuzzJIT](https://github.com/SpaceNaN/fuzzjit): It is a fuzzing tool for JavaScript engines JIT compiler, built on top of Fuzzilli. I was the only student involved in this project. The main contributors to this work are my mentor and zhiyi. I was responsible for some of the experimental parts of this project, including the code coverage comparison test.

