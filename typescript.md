## TYPESCRIPT

##  1. Data Types

### Any
* **What:** A type that allows a variable to hold any value, bypassing type-checking.
* **Why:** Useful when migrating JavaScript code or dealing with dynamic content where the type is unknown. (Use sparingly).
* **How:** `let data: any = "Hello"; data = 42;`

### String
* **What:** Represents textual data.
* **Why:** To ensure variables intended for text don't accidentally receive numbers or objects.
* **How:** `let name: string = "Abu";`

### Number
* **What:** Represents both integers and floating-point values.
* **Why:** Prevents mathematical errors by ensuring only numeric values are used.
* **How:** `let price: number = 99.99;`

### Boolean
* **What:** Represents `true` or `false`.
* **Why:** Essential for logic, flags, and conditional statements.
* **How:** `let isActive: boolean = true;`

### Null / Undefined
* **What:** `null` represents an intentional absence of value; `undefined` means a variable has been declared but not assigned.
* **Why:** Helps handle empty states safely, especially with `strictNullChecks` enabled.
* **How:** `let user: string | null = null;`

### Array
* **What:** A collection of values of the same type.
* **Why:** To manage lists of data with type safety for every element.
* **How:** `let scores: number[] = [10, 20, 30];` or `Array<number>`.

### Tuple
* **What:** A fixed-length array where each element has a specific type.
* **Why:** Useful for returning multiple related values (like coordinates or key-value pairs).
* **How:** `let userRole: [number, string] = [1, "Admin"];`

### Object
* **What:** Represents a non-primitive type (anything that isn't string, number, etc.).
* **Why:** To define structures for complex data entities.
* **How:** `let point: { x: number, y: number } = { x: 10, y: 20 };`

### Enum
* **What:** A way to define a set of named constants.
* **Why:** Improves code readability and prevents using "magic strings" or numbers.
* **How:**
```typescript 
            enum Status {
                Pending = "Pending",
                Active = "Active",
                Completed = "Completed"
            }

            let current: Status = Status.Active;
            console.log(current); // Output: "Active"

```

### Literal Types
* **What:** Restricts a variable to specific exact values.
* **Why:** To enforce strict allowed values (like a "status" or "theme").
* **How:** `let direction: "left" | "right" = "left";`

### Void
* **What:** Used as a return type for functions that return nothing.
* **Why:** Explicitly states that a function's side effects are the goal, not a return value.
* **How:** `function log(msg: string): void { console.log(msg); }`

### Never
* **What:** Represents values that will *never* occur (e.g., a function that always throws an error).
* **Why:** Useful for exhaustive type checking in complex unions.
* **How:** `function error(msg: string): never { throw new Error(msg); }`

### JSON
* **What:** JavaScript Object Notation; in TS, it's often handled via `JSON.parse` which returns `any` (or a typed interface).
* **Why:** For data exchange between a client and server.
* **How:** `const data: User = JSON.parse(jsonString);`

---

## 🟡 2. Functions & Logic
Defining how data moves and transforms.

### Function
* **What:** A block of code designed to perform a task, with typed inputs/outputs.
* **Why:** Ensures the correct data is passed in and expected data comes out.
* **How:** `function add(a: number, b: number): number { return a + b; }`

### Union
* **What:** Allows a variable to be one of several types.
* **Why:** Great for handling variables that can naturally hold different formats.
* **How:** `let id: string | number = "101";`

### Intersection
* **What:** Combines multiple types into one.
* **Why:** To merge properties from different interfaces into a single object.
* **How:** `type AdminUser = User & Permissions;`

### Type Alias
* **What:** A custom name for a type definition using `type`.
* **Why:** To simplify complex types and reuse them throughout the code.
* **How:** `type Point = { x: number; y: number; };`

### Interface
* **What:** A contract defining the shape an object must follow.
* **Why:** Highly extensible and ideal for defining public APIs or class structures.
* **How:** `interface User { id: number; name: string; }`

### Optional Properties
* **What:** Properties marked with `?` that may or may not exist.
* **Why:** To handle data structures where some fields are not always available.
* **How:** `interface Profile { bio?: string; age: number; }`

### Readonly
* **What:** A modifier that makes a property immutable after its first assignment.
* **Why:** Protects data integrity by preventing accidental modifications.
* **How:** `interface Config { readonly apiKey: string; }`

### Type Assertion
* **What:** Manually telling the compiler to treat a value as a specific type.
* **Why:** Used when you know more about the type than TypeScript does (e.g., DOM elements).
* **How:** `const input = document.getElementById("input") as HTMLInputElement;`

### Type Guards
* **What:** Logic to check the type of a variable at runtime.
* **Why:** Safely narrows down a union type so you can access specific properties.
* **How:** `if (typeof val === "string") { console.log(val.toUpperCase()); }`

### Async / Await & Promise
* **What:** Tools for handling asynchronous operations.
* **Why:** Provides a clean, readable way to handle API calls or timers.
* **How:** 
```typescript
        async function getData(): Promise<string> { 
            return "Done"; 
        }
```

### Yield
* **What:** Used in generator functions to produce a sequence of values.
* **Why:** Memory-efficient way to handle large datasets or iterative processes.
* **How:** `function* count() { yield 1; yield 2; }`

---

## 🟠 3. Classes & Object-Oriented Features
Building structured, reusable components.

### Class & Constructor
* **What:** A template for creating objects. The constructor initializes properties.
* **Why:** Provides encapsulation and reusable blueprints for data and behavior.
* **How:**
```typescript
class Car {
  carname: string;   // property declared

  constructor(carname: string) {
    this.carname = carname;  // property initialized
  }
}

let c1 = new Car("Toyota");
console.log(c1.carname); // "Toyota"

}
```

### Access Modifiers
* **What:** `public` (default), `private` (internal only), and `protected` (internal + subclasses).
* **Why:** Controls visibility and protects sensitive internal logic.
* **How:** `private engineId: string;`

### Inheritance (extends)
* **What:** Creating a new class based on an existing one.
* **Why:** Promotes code reuse and logical hierarchy.
* **How:** `class ElectricCar extends Car { ... }`

### Abstract Class
* **What:** A base class that cannot be instantiated on its own.
* **Why:** To define a common template for other classes to follow.
* **How:** `abstract class Shape { abstract getArea(): number; }`

### Implements
* **What:** Forces a class to follow the structure of an interface.
* **Why:** Ensures that different classes provide the same set of methods/properties.
* **How:** `class UserProfile implements Identifiable { id: string; }`

### Static
* **What:** Properties or methods that belong to the class itself, not instances.
* **Why:** For utility functions or shared constants.
* **How:** `static companyName = "Tech Corp";`

### Getter / Setter
* **What:** Intercepts access to an object's property.
* **Why:** To add validation or transformation logic when reading/writing data.
* **How:** `get price() { return this._price; }`

### Decorators
* **What:** Special declarations that can be attached to classes or methods.
* **Why:** To modify or observe behavior at runtime (metadata).
* **How:** `@sealed class MyClass {}`

---

## 🔵 4. Advanced Types & Utilities
Metaprogramming and complex type manipulation.

### Generics
* **What:** Using type variables (like `<T>`) to create reusable components.
* **Why:** To write functions that work with multiple types without losing type safety.
* **How:** `function wrap<T>(val: T): T { return val; }`

### keyof & typeof
* **What:** `keyof` gets object keys as a union; `typeof` gets the type of a variable.
* **Why:** To dynamically derive types from existing data or structures.
* **How:** `type UserKeys = keyof User;`

### Mapped & Conditional Types
* **What:** Creating new types by transforming or checking conditions on existing ones.
* **Why:** Allows for highly dynamic and flexible type definitions.
* **How:** `type IsString<T> = T extends string ? true : false;`

### Utility Types
* **What:** Built-in helpers for common transformations.
* **Why:** Saves time on common type tasks.
* **Examples:**
    * `Partial<T>`: Makes all properties optional.
    * `Required<T>`: Makes all properties required.
    * `Pick<T, K>`: Creates a type by picking specific keys.
    * `Omit<T, K>`: Creates a type by removing specific keys.
    * `Record<K, V>`: Creates an object type with specific keys and values.

---

## 🟣 5. Project & Configuration
Managing the TypeScript environment.

### Module
* **What:** Code organization using `import` and `export`.
* **Why:** Keeps the codebase maintainable and prevents global scope pollution.
* **How:** `import { User } from "./models";`

### TSConfig
* **What:** The `tsconfig.json` file controlling compiler settings.
* **Why:** To customize how TypeScript compiles into JavaScript.

### Strict Mode
* **What:** A setting (`"strict": true`) that enables all strict type-checking rules.
* **Why:** Catches the maximum number of potential bugs during development.

### Declaration File (.d.ts)
* **What:** Files containing only type information, no implementation.
* **Why:** Provides types for plain JavaScript libraries.

---

## 🟤 6. Control Flow
Standard logic structures in a typed environment.

### Loops (For, While, For...of, For...in)
* **What:** Repeatedly executes blocks of code.
* **Why:** To process arrays, objects, or repeat tasks.
* **How:**
    * `for (let item of array)`: Best for values in an array.
    * `for (let key in object)`: Best for keys in an object.