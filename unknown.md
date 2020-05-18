## Unknown type

```ts
let userInput: unknown;
let userName: string;

userInput = 5; // no errors
userInput = 'Hello'; // no errors

userName = userInput; // gets an error because you can not inferr type for a variable typed as unknown
```