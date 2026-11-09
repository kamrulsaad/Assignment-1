# Type Narrowing in TypeScript

## Introduction

Sometimes a value can be more than one type. A parameter might be a string or a number. Type narrowing is how TypeScript figures out the exact type inside a block of code so we can use it safely.

## Narrowing With `typeof`

The `typeof` check works great for primitives like string, number, and boolean. Inside each branch, TypeScript is smart enough to know the real type.

```ts
// Example from problem 2
const processInput = (value: string | number | boolean): string | number => {
  if (typeof value === "string") {
    return value.trim().toLowerCase()
  } else if (typeof value === "number") {
    return value * 10
  } else return value ? "Active" : "Inactive"
}
```

## Narrowing With `instanceof`

When we work with classes, `instanceof` checks if a value came from a certain class. This is handy for errors or custom objects.

```ts
const handleYearInput = (input: Date | string): string => {
  if (input instanceof Date) {
    return input.getFullYear().toString();
  }
  return input;
}
```

## Narrowing With the `in` Operator

The `in` operator checks if a property exists on an object. It helps us tell two object shapes apart.

```ts
type Dog = { bark: () => void };
type Cat = { meow: () => void };

const speak = (pet: Dog | Cat): void => {
  if ("bark" in pet) {
    pet.bark();
  } else {
    pet.meow();
  }
}
```

## Conclusion

Narrowing helps keeping our code safe when a value has more than one possible type. With `typeof`, `instanceof`, and `in`, TypeScript stops us from calling the wrong method and we can catch mistakes early.
