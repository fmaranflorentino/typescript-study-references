# Generics

```ts
function merge<T, U>(objA: T, objB: U) {
  return Object.assign(objA, objB);
}

const mergedObj = merge({ name: "Flávio" }, { role: "JavaScript Developer" });
console.log(`${mergedObj.name} - ${mergedObj.role}`);
```
