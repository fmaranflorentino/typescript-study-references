## Union Types

Union types are flexible to accepted one more than one type.

```ts
function combineInputs(
  input1: number | string,
  input2: number | string
): number | string {
  let result;

  if (typeof input1 === "string" && typeof input2 === "string") {
    result = `Hello combine inputs ${input1}, ${input2}`;
    return result;
  }

  result = input1 + input2;
  return result;
}
```
