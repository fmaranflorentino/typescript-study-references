# Decorators

Decators run before a class instanciation

```ts
function Logger(constructor: Function) {
  console.log('Logger');
  console.log(constructor);
}

@Logger
class Person {
  name = 'Flávio';

  constructor() {
    console.log('Creating...');
  }
}

const person = new Person();

console.log(person);
```