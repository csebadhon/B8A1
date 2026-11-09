# Type Narrowing in TypeScript

## Introduction

Type narrowing means making a wide type more specific inside a block of code. For example, a value of type `string | number` can be treated as only a `string` after we check it. TypeScript understands these checks and gives us safe autocomplete and fewer errors.

## Using `typeof`

The `typeof` check is the simplest way to narrow primitive types.

```ts
function printValue(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value.toFixed(2);
}
```

Inside the `if`, TypeScript knows `value` is a string. After it, the value must be a number.

## Using `instanceof`

The `instanceof` operator works with classes, so it is good for checking objects like errors or dates.

```ts
function showError(error: Error | string): string {
  if (error instanceof Error) {
    return error.message;
  }
  return error;
}
```

## Using the `in` Operator

The `in` operator checks if a property exists in an object. It helps when we have a union of different object types.

```ts
type Dog = { bark: () => void };
type Bird = { fly: () => void };

function move(pet: Dog | Bird): void {
  if ("bark" in pet) {
    pet.bark();
  } else {
    pet.fly();
  }
}
```

## Conclusion

Type narrowing lets us work safely with union types without using `any`. I think `typeof` is good for primitives, `instanceof` for classes, and `in` for object shapes. Using them makes our code cleaner and safer.
