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

I'm unfamiliar with the WebAssembly vulnerability exploit, so I don't know how to do anything with them yet. 

## FINISHED
### PatchFuzz: Patch Fuzzing for JavaScript Engines
[PatchFuzz](https://github.com/marckwei/patchFuzz): I am a major contributor to this project, and the code will be available to the public after the paper has been accepted.

The workflow of PatchFuzz:
![The workflow of PatchFuzz.](/images/patchfuzz_workflow.png)

Here are two bugs to share:

<table>
<tr>
<th>CVE-2020-9983</th>
<th>CVE-2020-9802</th>
</tr>
<tr>
<td>
<pre>
const ITERATIONS=1000000;
function f(n){
	n&=0xffffffff
	if(n<-1){
		let v=(-n)&0xffffffff;
		let i=Math.abs(n);
		let arr=new Array(10);
		arr.fill(42.42);
		if(i<arr.length){
			return arr[i];
		}
	}
}
for(let i=0;i<ITERATIONS;i++){
	let isLastIteration=
		i==ITERATIONS-1;
	let n=-(i%10);
	if(isLastIteration){
		n=-2147483648;
	}
	f(n);
}
</pre>
</td>
<td>

<pre>
const ITERATIONS=1000000;
function f(n){
	n&=<font color="red">0xffffffff-1</font>
	if(n<-1){
		let v=(-n)&0xffffffff;
		let i=Math.abs(n);
		let arr=new Array(10);
		arr.fill(42.42);
		if(i<arr.length){
			return arr[i];
		}
	}
}
for(let i=0;i<ITERATIONS;i++){
	let isLastIteration=
		i==ITERATIONS-1;
	let n=-(i%10);
	if(isLastIteration){
		n=-2147483648;
	}
	f(n);
}
</pre>

</td>
</tr>
</table>

### FuzzJIT: Oracle-Enhanced Fuzzing for JavaScript Engine JIT Compiler
[FuzzJIT](https://github.com/SpaceNaN/fuzzjit): It is a fuzzing tool for JavaScript engines JIT compiler, built on top of [Fuzzilli](https://github.com/googleprojectzero/fuzzilli). I was the only student involved in this project. The main contributors to this work are [my mentor](https://zhunki.github.io/index.html) and zhiyi. I was responsible for the calculation of some evaluative metrics, such as code coverage. I also used FuzzJIT to find several interesting logic bugs.

The workflow of FuzzJIT:
![The workflow of FuzzJIT.](/images/fuzzjit_workflow.png)

Here are two bugs to share:

1. v8_unsigned_number_optimization (I forgot to submit it.)
```javascript
function opt(){
	var a=new Float32Array(3300000000);
	a[-1000000000]=666;
	var b=a[-1000000000];
	var c=a[3294967296];// -1000000000 = u3294967296
	for(let i=1;i<1000;i++){
	}
	return c;
}
opt();
print(opt()); // output: 0
%OptimizeFunctionOnNextCall(opt);
print(opt()); // output: 666
```
2. jsc_issue_228068
```javascript
function opt() {
return parseInt ("−0");
}
let r1 = opt() ;
print (Object. is(r1 , −0)); // output : True
for ( let i = 0; i < 1000; i++) {
opt() ;
}
let r2 = opt() ;
print (Object. is(r2 , −0)); // output : False
```