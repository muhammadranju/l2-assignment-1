# Blog Posts

<!-- Blog Posts 1 -->

## 1. What are some differences between interfaces and types in TypeScript?

In TypeScript, both `interface` and `type` help you define the shape of objects. While they can often be used in similar ways, there are a few important differences to know.

---

### ✅ 1. Extending (Inheritance)

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

### ✅ 2. Declaration Merging

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

### ✅ 3. Use Cases

- Use **`interface`** when you're defining object shapes, especially with classes or APIs.
- Use **`type`** when you need to create **unions**, **intersections**, or **advanced types** like tuples and conditional types.

---

### ✅ 4. Which One Should You Use?

There’s no strict rule, but:

- Prefer `interface` for objects and class shapes.
- Use `type` when you need more flexibility or are working with non-object types.
