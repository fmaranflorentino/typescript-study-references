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

### Decorator Factories

```ts
function Logger(logString) {
  return function(constructor: Function) {
  console.log(logString);
  console.log(constructor);
  }
}

@Logger('Loggin person')
class Person {
  name = 'Flávio';

  constructor() {
    console.log('Creating...');
  }
}

const person = new Person();

console.log(person);
```

### useful decorators

```ts
function withTemplate(template: string, target: string) {
  return function (_: Function) {
    const targetElement = document.getElementById(target)!;
    targetElement.innterHTML = template; 
  }
}

@withTemplate('<h1>Hello app</h1>', 'app');
class HomeComponent {}
```
