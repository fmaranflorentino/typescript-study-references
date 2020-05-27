# Generics

```ts
function merge<T, U>(objA: T, objB: U) {
  return Object.assign(objA, objB);
}

const mergedObj = merge({ name: "Flávio" }, { role: "JavaScript Developer" });
console.log(`${mergedObj.name} - ${mergedObj.role}`);
```

## Constraints

Are used to restrict a generic typo

```ts
function merge<T extends object, U extends object>(objA: T, objB: U) {
  return Object.assign(objA, objB);
}
```

In the example above we can see that now the constraints restricts the T and U typo, we could use any kind of types

```ts
function merge<T extends object, U extends object>(objA: T, objB: U) {
function merge<T extends Person, U extends Job>(objA: T, objB: U) {
function merge<T extends string | number, U extends Job | Role>(objA: T, objB: U) {
  return Object.assign(objA, objB);
}
```

Another example

```ts
interface Lenghy {
  length: number;
}

function countAndDescribe<T extends Lenghy>(element: T): [T, string] {
  let description =
    element?.length > 0
      ? element.length === 1
        ? "Got 1 element."
        : `Got ${element.length} elementns.`
      : "Got no value.";

  return [element, description];
}
```

### Constraints - keyof

```ts
function extractAndConvert<T extends object, U extends keyof T>(
  objt: T,
  key: U
) {
  return obj[key];
}

extractAndConvert({ name: "Flávio" }, "name");
```

## Classes

```ts
class DataStorage<T extends string | number> {
  private data: T[] = [];

  addItem(item: T) {}

  removeItem(item: T) {}

  getItems(): T[] {}
}

const textStorage = new DataStorage<string>();
```
