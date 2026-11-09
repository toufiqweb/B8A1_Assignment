# Generics and Promise in TypeScript

## Introduction

Sometimes we want one function to work with many kinds of data. If we use `any`, TypeScript stops checking our code. Generics fix this problem.

## Explanation

A generic uses a letter like `T`. You can think of `T` as an empty box. The type goes into the box when we call the function.

```typescript
function getValue<T>(value: T): T {
  return value;
}

const number = getValue(100);
const text = getValue("Hello");
```

Here the same function works with a number and a string. We did not even write `<number>`, because TypeScript can guess it from the value.

Generics are very helpful with Promises. When we get data from an API, `Promise<T>` tells TypeScript what kind of data will come back.

```typescript
interface User {
  name: string;
}

async function fetchData<T>(url: string): Promise<T> {
  const response = await fetch(url);
  return response.json();
}

const user = await fetchData<User>("/api/user");
console.log(user.name);
```

TypeScript knows that `user` has a `name`. If I write `user.email` by mistake, I get an error before running the code, because `User` has no `email`. I can also use the same function to get products. I just write `fetchData<Product>` instead.

## Conclusion

Generics let us write one function for many types and still keep the checking. With `Promise<T>`, working with API data becomes safe and easier.
