# Type Aliases vs Interfaces in TypeScript

## Introduction

When I started learning TypeScript, `type` and `interface` looked like the same thing. Both let you describe the shape of an object. But they have some real differences, and knowing them properly helps pick the right one.

## How they are diffentiated

An `interface` is mainly built for describing objects and classes. You can also reopen it later and add more fields.

```ts
interface User {
  name: string;
}
interface User {
  age: number;
}
// User now has name and age
```

A `type` alias is more flexible. It can describe objects too, but it can also name unions, intersections, tuples, and primitives, which an interface cannot do.

```ts
type ID = string | number;
type Point = [number, number];
```

Both support extending. Interfaces use `extends`, while types use the `&` intersection operator to combine objects shape.

## When to Choose One

We can use `interface` for object shapes and class contracts, especially in larger codebase where merging or extending happens a lot and `type` when we need unions, tuples, or anything that is not a plain object.

## Conclusion

They overlap for objects, so either works there. The simple rule I follow: `interface` for object and class shapes, `type` for everything else.
