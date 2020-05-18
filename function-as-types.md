## Functions as type

```ts
const myAge = 23;
const dogAge = 4;

function add(y: number, x: number): number {
  return y + x;
}

const sumAge: (a, b) => number;
sumAge = add;

console.log(sumAge(myAge, dogAge));

function multiplicate(y: number, x: number, cb: (n: number) => void) {
  const result = y * x;
  cb(result);
}

multiplicate(10, 10, (res) => console.log(res))
```
