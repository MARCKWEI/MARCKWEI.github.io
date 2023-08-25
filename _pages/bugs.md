---
layout: archive
title: "BUGS"
permalink: /bugs/
author_profile: true
---

{% include base_path %}

Here are some of the bugs I found.

### WebKit/JavaScriptCore
* [Issue 255715](https://bugs.webkit.org/show_bug.cgi?id=255715): ASSERTION FAILED: edge->hasResult() in DFG::{anonymous}::Validate::validate().
* [Issue 255582](https://bugs.webkit.org/show_bug.cgi?id=255582): FunctionBind should fill BoundThis.
* [Issue 254574](https://bugs.webkit.org/show_bug.cgi?id=254574): Fix handleRecursiveTailCall for osr exit at op_tail_call.
* [Issue 245066](https://bugs.webkit.org/show_bug.cgi?id=245066): Array literal parsing should lex StringLiteral in the end of parsing.
* [CVE-2020-9983](https://bugs.webkit.org/show_bug.cgi?id=215536): B3 IntRange is incorrect for negative masks (which can be used to bypass the fix for [CVE-2020-9802](https://xz.aliyun.com/t/8913)).
 
### WebKit/WebAssembly
After communicating with WebKit's maintenance team, I was informed that they do not consider it a high priority to fix these bugs due to the additional runtime parameters they need to add to trigger the bugs. 

Therefore, even though they are marked as bugs, they will not be fixed in the near future.

* Issue 258499，258795，258796，258801，258804，258805: WebAssemblyGC is not ready yet

### Firefox/WebAssembly
Contrary to the attitude of the WebKit maintenance team, the bug I submitted to Firefox was quickly identified and fixed two weeks later, and the relevant code will be merged into the firefox118 branch.

* [Issue 1843295](https://bugzilla.mozilla.org/show_bug.cgi?id=1843295): \[WASM-GC\] Failure to serialize/deserialize type subtype declaration (will be merged in Firefox 118).
* [Issue 1845436](https://bugzilla.mozilla.org/show_bug.cgi?id=1845436): \[WASM-GC\] Canonical types should use type index of first occurence in module (will be merged in Firefox 118).

### [JerryScript](https://github.com/jerryscript-project/jerryscript)

- [CVE-2021-41751](https://github.com/jerryscript-project/jerryscript/pull/4797): In the Array.slice method when the engine uses fast arrays the "end" value was not updated if the input array's length changed (as same as CVE-2016-4622).
- [CVE-2023-30406](https://github.com/jerryscript-project/jerryscript/issues/5058): Assertion 'ecma_get_lex_env_type (lex_env_p) == ECMA_LEXICAL_ENVIRONMENT_DECLARATIVE' failed.
- [Issue 5057](https://github.com/jerryscript-project/jerryscript/issues/5057): Unstable segmentation fault.
- [Issue 5052](https://github.com/jerryscript-project/jerryscript/issues/5052): Stack-overflow in ecma_op_function_construct.
- [Issue 5051](https://github.com/jerryscript-project/jerryscript/issues/5051): Stack-overflow  in vm_loop.

### [Tengine](https://github.com/OAID/Tengine)
- [CVE-2020-28759](https://github.com/OAID/Tengine/issues/476): Constructed malicious input leading to a buffer overflow utilizing poor format checking.

### Some small targets
- [CVE-2020-1914](https://github.com/armink/struct2json/issues/13): Unsafe use of the `strcpy` function.
- [CVE-2020-35242,CVE-2020-35243,CVE-2020-35244,CVE-2020-35245](https://github.com/balloonwj/flamingo/issues/47): SQL injection.
- [CVE-2021-28013](https://github.com/qinguoyi/TinyWebServer/issues/45): SQL injection.
- [CVE-2021-28015](https://github.com/qinguoyi/TinyWebServer/issues/45): the length of a sql statement is not limited, causing heap overflow.
- [CVE-2021-28014](https://github.com/qinguoyi/TinyWebServer/issues/45): the length of a input is not limited, causing stack overflow.