## Interfaces

```ts

interface Named {
  readonly name: string;
}

interface Greetable extends Named {
  greet(msg: string): void;
}

class Person implements Greetable {
  constructor(public name: string)

  greet(msg: string) {
    console.log(msg);
  }
}
```

### Interfaces as function types

```ts
interface sum {
  (x: number, y: number): number;
}

let su: sum;
su = (n1, n2) => n1 + n2;
```
