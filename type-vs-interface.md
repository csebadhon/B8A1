# Type vs Interface in TypeScript

## Introduction

When I started learning TypeScript, I was confused about `type` and `interface`, because both can describe the shape of an object. They look similar, but they are different in some important ways. Let's look at them.

## Main Differences

An interface is mainly used for object shapes, and it can be extended with `extends`. A type alias is more flexible because it can also name unions, tuples and primitives.

```ts
interface User {
  name: string;
}
interface Admin extends User {
  level: number;
}

type Id = string | number;
type Point = [number, number];
```

Another big difference is declaration merging. If you write the same interface twice, TypeScript merges them into one. A type alias cannot be declared twice, so it gives an error.

```ts
interface Car {
  brand: string;
}
interface Car {
  year: number;
}
// Car now has both brand and year
```

Types can be combined using `&`, which is useful for building new shapes from old ones.

```ts
type Employee = User & { salary: number };
```

## When to Choose Which

I use `interface` for objects and classes, because it is easy to read and works well with `implements`. I use `type` when I need unions, tuples or intersections. The most important thing is to stay consistent in the same project.

## Conclusion

Both `type` and `interface` are useful, and for simple objects they work almost the same. Knowing merging, extending and union support helps you pick the right one.
