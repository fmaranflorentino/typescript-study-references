# Nullish Coaslescing (??)

When you want to make sure that some property is really NULL or UNDEFINED. Not zeros, not empty string.

```ts
const userName = '';

const storeUser = userName ?? 'DEFAULT';

console.log(storeUser);
```

The code above is going to print `empty string ''`

```ts
const userName = '';

const storeUser = userName || 'DEFAULT';

console.log(storeUser);
```

The code above is going to print `DEFAULT`
