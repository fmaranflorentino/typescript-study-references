# Decorators

Decators run before a class instanciation

```ts
function Logger(constructor: Function) {
  console.log("Logger");
  console.log(constructor);
}

@Logger
class Person {
  name = "Flávio";

  constructor() {
    console.log("Creating...");
  }
}

const person = new Person();

console.log(person);
```

### Decorator Factories

```ts
function Logger(logString) {
  return function (constructor: Function) {
    console.log(logString);
    console.log(constructor);
  };
}

@Logger("Loggin person")
class Person {
  name = "Flávio";

  constructor() {
    console.log("Creating...");
  }
}

const person = new Person();

console.log(person);
```

### Useful Decorators

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

### Property Decorators

```ts
function Log(target: any, propertyName: string | Symbol) {
  console.log(target, propertyName);
}

class Product {
  @Log
  title: string;

  private _price: number;

  constructor(public t: string, private p: number) {
    this.title = t;
    this._price = p;
  }

  set price(val: number) {
    this._price = val;
  }

  get price(): number {
    return this._price;
  }

  getPriceWithTax(tax: number) {
    return this._price * (1 + tax);
  }
}
```

## Accessor & Parameter Decorators

```ts
function Log(target: any, name: string, descriptor: PropertyDescriptor) {
  console.log("Accessor");
  console.log(target);
  console.log(name);
  console.log(descriptor);
}

function Log2(
  target: any,
  name: string | Symbol,
  descriptor: PropertyDescriptor
) {
  console.log("Method");
  console.log(target);
  console.log(name);
  console.log(descriptor);
}

function Log3(
  target: any,
  name: string | Symbol,
  position: number
) {
  console.log("parameter");
  console.log(target);
  console.log(name);
  console.log(position);
}

class Product {
  title: string;

  private _price: number;

  constructor(public t: string, private p: number) {
    this.title = t;
    this._price = p;
  }

  @Log
  set price(val: number) {
    this._price = val;
  }

  @Log2 getTax(@Log3 taxValue: number) {}

}
```

## When do decorators execute ? 

It not executes on runtime it executes when it's `defined` and decorators are not event listners . 
