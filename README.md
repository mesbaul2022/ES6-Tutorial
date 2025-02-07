# ES6-Tutorial
In modern JavaScript, `var`, `let`, and `const` are used to declare variables, but they differ in scoping, hoisting, and reassignment rules. Let’s break them down with examples based on your code:

---

### 1. **`var` (Function-Scoped)**
- **Scope**: Function-level (not block-level).
- **Hoisting**: Variables are hoisted and initialized with `undefined`.
- **Reassignment**: Allowed.
- **Redeclaration**: Allowed in the same scope.

**Example**:
```javascript
function sayHello() {
  for (var i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
  }
  console.log(i); // 5 (accessible because `var` is function-scoped)
}
sayHello();
```
- `i` is accessible **outside** the `for` loop because `var` is function-scoped. It exists throughout the entire function.

---

### 2. **`let` (Block-Scoped)**
- **Scope**: Block-level (e.g., inside `{}`).
- **Hoisting**: Hoisted but not initialized (cannot be accessed before declaration).
- **Reassignment**: Allowed.
- **Redeclaration**: Not allowed in the same scope.

**Example**:
```javascript
function sayHello() {
  for (let i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
  }
  console.log(i); // ❌ ReferenceError: `i` is not defined
}
sayHello();
```
- `i` is **not accessible outside** the `for` loop because `let` is block-scoped. The outer `console.log(i)` throws an error.

---

### 3. **`const` (Block-Scoped)**
- **Scope**: Block-level (like `let`).
- **Hoisting**: Hoisted but not initialized.
- **Reassignment**: **Not allowed** (value is constant).
- **Redeclaration**: Not allowed.

**Example**:
```javascript
function sayHello() {
  const PI = 3.14;
  PI = 3.1416; // ❌ TypeError: Assignment to constant variable

  for (const j = 0; j < 5; j++) { // ❌ TypeError: Assignment to constant variable
    console.log(j);
  }
}
sayHello();
```
- `const` variables cannot be reassigned. This makes them unsuitable for loop counters in traditional `for` loops (use `let` instead).  
- **Workaround for loops**: Use `const` in `for...of` loops (each iteration creates a new binding):
  ```javascript
  for (const num of [1, 2, 3]) {
    console.log(num); // 1, 2, 3
  }
  ```

---
1. **`var` Example**:
   - `i` is accessible outside the loop (prints `5`).
   - No error occurs because `var` is function-scoped.

2. **`let` Example**:
   - `i` is **not accessible** outside the loop (throws `ReferenceError`).
   - Fix: Avoid accessing `i` outside the loop block.

---

### Best Practices:
1. Use `const` by default for variables that don’t need reassignment.
2. Use `let` for variables that need reassignment (e.g., loop counters).
3. Avoid `var` in modern code to prevent unintended scope issues.


Here are the notes with suitable titles and short discussions for each topic based on your code:  

---

### 1. **Object Literals in JavaScript**  
In JavaScript, objects can be created using object literals, which provide a simple way to define key-value pairs.  

**Example:**  
```js
const person = {
  name: 'Muntasir',
  walk() {},
  talk() {}
};
```

---

### 2. **Accessing Object Properties**  
Object properties can be accessed using dot notation or bracket notation.  

**Example:**  
```js
person.talk(); // Dot notation
person.name = ''; // Modifying property using dot notation
```

---

### 3. **Dynamic Property Access**  
Bracket notation allows dynamic access to object properties using variables.  

**Example:**  
```js
const targetMember = 'name';
person[targetMember] = 'Muntasir';
```
Here, `targetMember` holds the property name, which is used dynamically to assign a value.  

---
Here are the notes with suitable titles and short discussions based on your code:  

---

### 1. **The `this` Keyword in JavaScript**  
In JavaScript, `this` refers to the object that is calling the function. When a method is called within an object, `this` refers to that object.  

**Example:**  
```js
const person = {
  name: "Mosh",
  walk() {
    console.log(this); // Refers to the 'person' object
  }
};

person.walk(); // Logs the 'person' object
```

---

### 2. **Losing `this` in Function Assignment**  
When a method is assigned to a variable, `this` may lose its reference to the original object.  

**Example:**  
```js
const walk = person.walk;
walk(); // `this` is now undefined or refers to the global object in non-strict mode
```

---

### 3. **Binding `this` with `.bind()`**  
The `.bind()` method is used to explicitly bind `this` to a specific object, ensuring it always refers to that object when the function is called.  

**Example:**  
```js
const walk = person.walk.bind(person);
walk(); // Ensures 'this' refers to 'person'
```

---
