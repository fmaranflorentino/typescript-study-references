## Never type

`never` type is used for code quality when you want to guarantee that the method will never return any value

```ts
function generateError(message: string, code: number): never {
  throw { message: message, code };
}

generateError("Internal server error", 500);
```
