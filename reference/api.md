---
layout: post.liquid
title: Reference - API
sort: 3.1
---

# API Reference

#### AstNode

Represents a node in the syntax tree. All nodes contain at least a type property.

```ts
type AstNode = {
  type: string;
  [key: string]: any;
};
```

#### AstNodeParser

Contract for a parser function. The function should be named after the AST node type. Binding a scopeBoundary field on the function will create a new scope for all variables defined inside the hieararchy.

```ts
type AstNodeParser = {
  (node: Omit<AstNode, "type">, options: AstNodeParserOptions): string;
  scopeBoundary?: boolean;
};
```

#### AstNodeParserOptions

Includes references to the transpile function and scope.

```ts
type AstNodeParserOptions = {
  transpile: TranspileFunction;
  scope: {
    variables: Record<string, any>;
    [key: string]: any;
  };
};
```

#### JspiclOptions

```ts
type JspiclOptions = {
  prettify?: boolean;
  customMappers?: Record<string, AstNodeParser>;
};
```

<ul class="argument-list">
  <li>
    <code>prettify: boolean = true</code>
    <p>
      Prettifies the transpiled code. By default, jspicl formats the Lua output for you but if performance ever
      becomes an issue you can turn this off by setting this to false.
    </p>
  </li>

  <li>
    <code>customMappers: Record&lt;string, TranspileFunction&gt;</code>
    <p>Custom handlers for transpiling expressions, declarations or statements.</p>
  </li>
</ul>

#### TranspileFunction

```ts
type TranspileFunction = (node: AstNode, options?: TranspileOptions) => string;
```

#### TranspileOptions

```ts
type TranspileOptions = { arraySeparator?: string };
```
