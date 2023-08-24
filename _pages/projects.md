---
layout: archive
title: "PROJECTS"
permalink: /projects/
author_profile: true
---

{% include base_path %}

Underway
======
Recently, I've turned my attention to **WebAssembly**, which I think has a lot of potential and is now supported by all major browsers. 

Therefore, it will be the next focus of my research. I've implemented a tool to fuzz WebAssembly parts of browsers, based on an idea presented at [Black Hat Asia 2023](https://www.blackhat.com/asia-23/briefings/schedule/#attacking-the-webassembly-compiler-of-webkit-30926). 
My tool has detected 9 unique crashes in JavaScriptCore and SpiderMonkey in their WebAssembly parts, all of which have been identified as vulnerabilities by the vendors. 

However, I'm relatively new to exploiting WebAssembly vulnerabilities, and I don't know how to do anything with them yet. If you are interested in WebAssembly, please feel free to contact me.

Finished
======
[FuzzJIT](https://github.com/SpaceNaN/fuzzjit): It is a fuzzing tool for JavaScript engines JIT compiler, built on top of Fuzzilli. I was the only student involved in this project. The main contributors to this work are my mentor and zhiyi. I was responsible for some of the experimental parts of this project, including the code coverage comparison test.

[PatchFuzz](https://github.com/marckwei/patchFuzz): I am the major contributor to this project, and the code will be available to the public after the paper has been accepted.