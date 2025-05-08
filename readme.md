# Blog Posts

<!-- Blog Posts 1 -->

## 1. What are some differences between interfaces and types in TypeScript?

In TypeScript, both `interface` and `type` help you define the shape of objects. While they can often be used in similar ways, there are a few important differences to know.

---

### 1. Extending (Inheritance)

- **`interface`** uses `extends` to inherit:

```ts
interface Animal {
  name: string;
}

interface Dog extends Animal {
  breed: string;
}
```

- **`type`** uses `&` to combine types:

```ts
type Animal = {
  name: string;
};

type Dog = Animal & {
  breed: string;
};
```

---

### 2. Declaration Merging

- **`interface`** supports merging. You can define it more than once, and TypeScript will combine the definitions:

```ts
interface User {
  name: string;
}
interface User {
  age: number;
}
// User = { name: string; age: number }
```

- **`type`** does **not** support merging. Declaring the same type twice causes an error.

---

### 3. Use Cases

- Use **`interface`** when you're defining object shapes, especially with classes or APIs.
- Use **`type`** when you need to create **unions**, **intersections**, or **advanced types** like tuples and conditional types.

---

### 4. Which One Should You Use?

There’s no strict rule, but:

- Prefer `interface` for objects and class shapes.
- Use `type` when you need more flexibility or are working with non-object types.

<!-- Blog Posts 2 -->

## 2. What is the use of the `keyof` keyword in TypeScript? Provide an example.

If you're new to TypeScript, you might have come across the `keyof` keyword and wondered what it does. Let me explain it to you in simple terms.

### What is `keyof`?

In TypeScript, **`keyof`** is used to get the type of the **keys** of an object. It returns a **union type** of all the keys in a given type, making your code safer and more flexible.

### How Does `keyof` Work?

Let’s say you have an interface `Person`:

```ts
interface Person {
  name: string;
  age: number;
}

type PersonKeys = keyof Person; // "name" | "age"
```

In this case, `keyof Person` will give you a union type of the keys—`"name"` and `"age"`.

### Real-World Example: Dynamic Key Access

You can use `keyof` to create functions that dynamically access object properties, ensuring type safety:

```ts
interface Product {
  id: number;
  name: string;
}

function getProperty<T>(obj: T, key: keyof T) {
  return obj[key];
}

const product = { id: 1, name: "Laptop" };
console.log(getProperty(product, "name")); // Output: "Laptop"
```

Here, the `key` parameter is guaranteed to be a valid key of `Product`, so you can't accidentally pass an invalid property.

### Conclusion

The `keyof` keyword in TypeScript helps you work with object keys in a type-safe way, making your code more reliable and easier to maintain. It ensures that you can only access valid keys from an object, preventing runtime errors.
