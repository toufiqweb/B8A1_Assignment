# Type vs Interface in TypeScript

## Introduction

In TypeScript, interface and type are used to define data structures. Both are used to define the data an object can have and keep the code organized.

## Explanation

An interface is used to define the structure of an object. We can also extend an existing interface or declare the same interface multiple times to add more properties.

```typescript
interface User {
  name: string;
}

interface User {
  age: number;
}
```

A type can do more things. It can hold objects, but also unions like "success" | "error". But you cannot write the same type name two times. It will give an error.

```typescript
type Status = "success" | "error";

type Product = {
  name: string;
  price: number;
};
```

To add more properties, an interface uses extends and a type uses &.

```typescript
interface Admin extends User {
  role: string;
}

type AdminUser = User & {
  role: string;
};
```

Interface is mainly used for objects, while type is useful for unions, intersections, and other types.

## Conclusion

Both type and interface are useful for defining object structures. They work similarly in many cases. Use interface for object structures and type when you need features like unions and intersections.
