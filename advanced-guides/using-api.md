---
layout: post.liquid
title: Advanced Guide - Using the API
sort: 2.1
---

# Using the API

The API can be used for transpiling JavaScript into the subset of Lua that PICO-8 uses.

## Installation

```bash-with-tab
npm install jspicl --save
```

## Usage

```js-with-tab
import {jspicl} from "jspicl";

const javascriptCode = `
  // Your code here
`;

const {code, polyfills} = jspicl(javascriptCode);
console.log(code);
```

## Known limitations

|                  |                                                                                                                                                                                 |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ES2015+          | Not all ES2015+ features are supported. Run your code through a transpiler first such as [babel](https://www.npmjs.com/package/babel) or [esbuild](https://esbuild.github.io/). |
| prototype chains | Not supported                                                                                                                                                                   |
| Array methods    | Not all prototype methods have been polyfilled yet.                                                                                                                             |
| Math.max         | Only supports two arguments.                                                                                                                                                    |
| AST              | Not all declarations, expressions and statements have been implemented. More will be added as needed.                                                                           |
