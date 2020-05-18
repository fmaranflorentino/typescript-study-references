## Literal Types

```ts
function combineValues(
  input1: number | string,
  input2: number | string,
  operator: "as-text" | "as-number"
): number | string {
  let result;

  if (operator === "as-number") {
    result = +input1 + +input2;
    return result;
  }

  result = `Hellow strings ${input1}${input2}`;
  return result;
}
```
