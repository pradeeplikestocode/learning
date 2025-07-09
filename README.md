# Java Collections Framework – Interview Cheat Code

## ✅ What is the Collections Framework?

A set of **classes and interfaces** in Java that help store and manipulate groups of data as a single unit. Part of `java.util` package.

---

## ✅ Key Interfaces

* `List` – Ordered, allows duplicates
* `Set` – Unordered, no duplicates
* `Queue` – FIFO structure
* `Map` – Key-value pairs

---

## ✅ Implementations Cheat Table

| Interface | Implementation       | Thread Safe | Ordered | Sorted |
| --------- | -------------------- | ----------- | ------- | ------ |
| List      | ArrayList            | ❌           | ✅       | ❌      |
| List      | LinkedList           | ❌           | ✅       | ❌      |
| Set       | HashSet              | ❌           | ❌       | ❌      |
| Set       | TreeSet              | ❌           | ✅       | ✅      |
| Map       | HashMap              | ❌           | ❌       | ❌      |
| Map       | TreeMap              | ❌           | ✅       | ✅      |
| Map       | LinkedHashMap        | ❌           | ✅       | ❌      |
| Map       | ConcurrentHashMap    | ✅           | ❌       | ❌      |
| List      | CopyOnWriteArrayList | ✅           | ✅       | ❌      |

---

## ✅ Common Methods

* `add()`, `remove()`, `contains()`
* `get()`, `put()`, `size()`, `clear()`
* `iterator()`, `entrySet()`, `keySet()`, `values()`

---

## ✅ Iteration Techniques

```java
// Enhanced for-loop
for(String item : list) {
    System.out.println(item);
}

// Iterator
Iterator<String> it = list.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}
```

---

## ✅ Synchronization

* Use `Collections.synchronizedList(list)`
* Prefer `ConcurrentHashMap` / `CopyOnWriteArrayList` for thread safety

---

## ✅ Best Practices

* Use interfaces in declarations: `List<String> l = new ArrayList<>();`
* Pick the right structure: e.g., `HashMap` for fast lookup, `TreeMap` for sorting
* Prefer `LinkedHashMap` if you need order of insertion
* Avoid resizing inside loops for `ArrayList`

---

## ✅ Utility Classes

* `Collections`: `sort()`, `reverse()`, `shuffle()`
* `Arrays`: `asList()`, `sort()`

---

## ✅ Example

```java
List<String> fruits = new ArrayList<>();
fruits.add("Apple");
fruits.add("Banana");
Collections.sort(fruits);

Map<Integer, String> users = new HashMap<>();
users.put(1, "Alice");
users.put(2, "Bob");
```

---

## 💡 Pro Tip for Interviews

Always mention the **Big O complexity**, **thread-safety**, and **null support** when asked to choose a collection!


# Java Stream API – Cheat Code with Methods & Examples

## ✅ What is Stream API?

Introduced in Java 8, the Stream API enables functional-style operations on collections and sequences of elements.

---

## ✅ Common Stream Methods

| Method                | Purpose                               |
| --------------------- | ------------------------------------- |
| `filter(Predicate)`   | Filter elements based on condition    |
| `map(Function)`       | Transform each element                |
| `forEach(Consumer)`   | Iterate over elements                 |
| `collect(Collectors)` | Collect result into a list, map, etc. |
| `sorted()`            | Sort the stream                       |
| `distinct()`          | Remove duplicates                     |
| `limit(n)`            | Limit number of results               |
| `skip(n)`             | Skip first n elements                 |
| `reduce()`            | Combine elements into one             |
| `count()`             | Count elements                        |
| `anyMatch()`          | Checks if any element matches         |
| `allMatch()`          | Checks if all elements match          |
| `noneMatch()`         | Checks if no element matches          |

---

## ✅ Basic Example

```java
list.stream()
    .filter(condition)
    .map(transformation)
    .forEach(action);
```

---

## ✅ Grouping & Counting Example

```java
stream.collect(Collectors.groupingBy(keyExtractor, Collectors.counting()));
```

---

## ✅ Collectors Examples

```java
// To List
stream.map(mapper).collect(Collectors.toList());

// Grouping with Mapping
stream.collect(Collectors.groupingBy(keyExtractor,
    Collectors.mapping(valueMapper, Collectors.toList())));
```

---

## ✅ Reduce Example

```java
stream.reduce(identity, accumulator);
```

---

## ✅ Parallel Stream Example

```java
stream.parallel().forEach(action);
```

---

## 💡 Pro Tip for Interviews

Mention:

* Streams are **lazy** and **don't modify source**
* Use **parallelStream()** for better performance on large data sets
* Stream API is part of **java.util.stream** package


# Java Exceptions and Fail-Fast vs Fail-Safe – Cheat Code

## ✅ Types of Exceptions in Java

### Checked Exceptions

* Known at **compile time**.
* Must be either caught or declared with `throws`.
* Examples: `IOException`, `SQLException`

### Unchecked Exceptions

* Known at **runtime**.
* Extends `RuntimeException`, not required to be caught.
* Examples: `NullPointerException`, `ArithmeticException`, `ArrayIndexOutOfBoundsException`

### Error

* Serious problems, usually not handled in code.
* Examples: `OutOfMemoryError`, `StackOverflowError`

---

## ✅ Fail-Fast vs Fail-Safe

### Fail-Fast

* Fails immediately on concurrent modification.
* Throws `ConcurrentModificationException`.
* Examples: `ArrayList`, `HashMap` (iterators)
* Works on original collection.

```java
for (String item : list) {
    list.remove(item); // Throws exception
}
```

### Fail-Safe

* Allows modification during iteration.
* Uses clone or copy under the hood.
* No `ConcurrentModificationException`.
* Examples: `ConcurrentHashMap`, `CopyOnWriteArrayList`

```java
for (String item : copyOnWriteList) {
    copyOnWriteList.remove(item); // Safe
}
```

---

## 💡 Pro Tip for Interviews

* Mention exception hierarchy: `Throwable > Exception > Checked/Unchecked`
* Fail-Fast is faster but unsafe in concurrent mods.
* Fail-Safe is safe but less performant.


# Java Thread Programming – Cheat Code

## ✅ Creating Threads

### 1. Extend Thread class

```java
class MyThread extends Thread {
  public void run() {
    System.out.println("Thread running");
  }
}
new MyThread().start();
```

### 2. Implement Runnable interface

```java
class MyRunnable implements Runnable {
  public void run() {
    System.out.println("Runnable running");
  }
}
new Thread(new MyRunnable()).start();
```

### 3. Using Lambda

```java
new Thread(() -> System.out.println("Lambda Thread")).start();
```

---

## ✅ Thread Lifecycle

`NEW → RUNNABLE → RUNNING → BLOCKED/WAITING → TERMINATED`

---

## ✅ Thread Methods

```java
start()     // starts a thread
run()       // contains code to execute
sleep(ms)   // pause execution
join()      // wait for another thread to finish
yield()     // suggest thread switch
interrupt() // interrupts a sleeping/waiting thread
```

---

## ✅ Synchronization

```java
synchronized void method() { ... }

synchronized(obj) {
  // block-level sync
}
```

---

## ✅ Volatile vs Synchronized

| Feature    | volatile | synchronized |
| ---------- | -------- | ------------ |
| Atomicity  | ❌        | ✅            |
| Visibility | ✅        | ✅            |
| Locking    | ❌        | ✅            |

---

## ✅ wait(), notify(), notifyAll()

* Used for inter-thread communication.

```java
synchronized(obj) {
  obj.wait();       // wait and release lock
  obj.notify();     // wake up one waiting thread
  obj.notifyAll();  // wake up all
}
```

---

## ✅ ThreadPool (ExecutorService)

```java
ExecutorService executor = Executors.newFixedThreadPool(5);
executor.submit(() -> System.out.println("Task"));
executor.shutdown();
```

---

## 💡 Pro Tips for Interviews

* Prefer `Runnable` over `Thread` inheritance.
* Use `ExecutorService` for managing multiple threads.
* Always call `start()` not `run()` to create a new thread.
* Use `synchronized`/locks to prevent race conditions.
* Mention thread safety and visibility concerns.


# HTML & CSS – Cheat Code for Interviews

## ✅ HTML Essentials

### Basic Tags

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <h1>Heading</h1>
    <p>Paragraph</p>
    <a href="#">Link</a>
    <img src="image.jpg" alt="desc">
    <ul><li>Item</li></ul>
    <div>Container</div>
  </body>
</html>
```

### Semantic Tags

```html
<header>, <main>, <footer>, <article>, <section>, <nav>, <aside>
```

### Forms

```html
<form>
  <input type="text">
  <input type="email">
  <input type="submit">
</form>
```

---

## ✅ CSS Essentials

### Selectors

```css
*       /* all elements */
h1      /* by tag */
#id     /* by id */
.class  /* by class */
div > p /* child selector */
```

### Box Model

```css
box-sizing: border-box;
margin, border, padding, content
```

### Positioning

```css
position: static | relative | absolute | fixed | sticky;
top, bottom, left, right
```

### Flexbox

```css
display: flex;
justify-content: center | space-between | space-around;
align-items: center | flex-start | flex-end;
flex-direction: row | column;
```

### Grid

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 10px;
```

### Media Queries

```css
@media (max-width: 600px) {
  body { font-size: 14px; }
}
```

---

## ✅ CSS Hierarchy & Specificity

### Specificity Order

| Selector Type      | Specificity Score |
| ------------------ | ----------------- |
| Inline styles      | 1000              |
| IDs                | 100               |
| Classes/Attributes | 10                |
| Elements/Tags      | 1                 |

### Example

```css
h1 { color: red; }          /* Score: 1 */
.title { color: blue; }     /* Score: 10 */
#main { color: green; }     /* Score: 100 */
style="color: purple;"      /* Score: 1000 */
```

* The rule with the highest specificity wins.
* If specificity is the same, the last declared rule wins.

### 💡 Tips

* Avoid using inline styles; they have the highest specificity.
* Prefer class selectors for modular CSS.
* Use `!important` only when necessary – it overrides all.

---

## 💡 Pro Tips for Interviews

* Use semantic tags for accessibility and SEO.
* Understand CSS specificity: inline > id > class > tag.
* Prefer `rem`/`em` over `px` for responsive design.
* Flexbox for layout, Grid for structured components.
* Always use `box-sizing: border-box;` to avoid layout issues.


# React Common Hooks – Cheat Code

## ✅ useState

```js
const [state, setState] = useState(initialValue);
```

---

## ✅ useEffect

```js
useEffect(() => {
  // side effect
}, [dependencies]);
```

---

## ✅ useContext

```js
const value = useContext(MyContext);
```

---

## ✅ useRef

```js
const ref = useRef(initialValue);
```

---

## ✅ useMemo

```js
const memoizedValue = useMemo(() => computeFn(a, b), [a, b]);
```

---

## ✅ useCallback

```js
const memoizedCallback = useCallback(() => doSomething(a), [a]);
```

---

## ✅ useReducer

```js
const [state, dispatch] = useReducer(reducerFn, initialState);
```

---

## 💡 Pro Tips for Interviews

* Mention `useEffect` dependencies carefully to avoid infinite loops.
* `useMemo` and `useCallback` are performance optimizers.
* `useRef` is also used to access DOM nodes directly.
* `useReducer` is preferred when managing complex state transitions.


# React Routing – Cheat Code

## ✅ Setup (React Router DOM)

```bash
npm install react-router-dom
```

---

## ✅ Basic Routing

```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## ✅ Navigation

```jsx
import { Link } from 'react-router-dom';

<Link to="/about">About</Link>
```

---

## ✅ useNavigate

```jsx
import { useNavigate } from 'react-router-dom';

const navigate = useNavigate();
navigate('/about');
```

---

## ✅ useParams

```jsx
import { useParams } from 'react-router-dom';

const { id } = useParams();
```

---

## ✅ Nested Routes

```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="stats" element={<Stats />} />
</Route>
```

---

## 💡 Pro Tips for Interviews

* Always use `BrowserRouter` once at the root level.
* Use `useParams` for dynamic route data.
* `useNavigate` replaces `useHistory` in v6.
* Handle 404 routes with `path="*"`.
* Group related pages with nested routes.


# JavaScript Basics – Cheat Sheet (Topics Only)

## ✅ Data Types

* Primitive Types
* Reference Types

## ✅ Variables

* var
* let
* const

## ✅ Operators

* Arithmetic
* Assignment
* Comparison
* Logical
* Ternary

## ✅ Control Flow

* if / else
* switch
* for / for...of / for...in
* while / do...while
* break / continue

## ✅ Functions

* Function Declaration
* Function Expression
* Arrow Functions
* IIFE (Immediately Invoked Function Expression)
* Callback Functions

## ✅ Objects

* Object Literals
* Property Access
* Destructuring
* Object Methods
* `this` Keyword

## ✅ Arrays

* Array Methods (map, filter, reduce, forEach, etc.)
* Destructuring
* Spread & Rest

## ✅ ES6+ Features

* let & const
* Arrow Functions
* Template Literals
* Default Parameters
* Destructuring
* Spread / Rest Operators
* Modules (import/export)
* Optional Chaining
* Nullish Coalescing

## ✅ Asynchronous JavaScript

* Callbacks
* Promises
* async / await
* setTimeout / setInterval

## ✅ Error Handling

* try / catch / finally
* throw

## ✅ DOM Manipulation

* Selecting Elements
* Event Handling
* Modifying Elements

## ✅ Miscellaneous

* Hoisting
* Closures
* Scope (Block, Function, Global)
* Event Loop
* Strict Mode
* Type Coercion
* JSON

---

## 💡 Pro Tip

Use this as a checklist to revise core JavaScript before interviews.


# TypeScript Cheat Code – Quick Reference for Interviews

## ✅ Basic Types

```ts
let id: number = 1;
let name: string = 'John';
let isActive: boolean = true;
let tags: string[] = ['ts', 'js'];
let scores: Array<number> = [10, 20];
```

---

## ✅ Tuple

```ts
let person: [string, number] = ['Alice', 30];
```

---

## ✅ Enum

```ts
enum Role { Admin, User, Guest }
let role: Role = Role.User;
```

---

## ✅ Any, Unknown, Void, Never

```ts
let data: any;
let input: unknown;
function log(): void {}
function error(): never { throw new Error('Oops'); }
```

---

## ✅ Interfaces

```ts
interface User {
  id: number;
  name: string;
  isActive?: boolean; // optional
}

const user: User = { id: 1, name: 'John' };
```

---

## ✅ Type Aliases

```ts
type ID = number | string;
let userId: ID = 101;
```

---

## ✅ Functions

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}

const add = (a: number, b: number): number => a + b;
```

---

## ✅ Type Assertions

```ts
let someValue: unknown = 'hello';
let strLength = (someValue as string).length;
```

---

## ✅ Generics

```ts
function identity<T>(arg: T): T {
  return arg;
}
```

---

## ✅ Utility Types

```ts
Partial<T>, Required<T>, Readonly<T>, Pick<T, K>, Omit<T, K>
```

---

## ✅ Classes

```ts
class Person {
  constructor(public name: string, private age: number) {}

  greet() {
    return `Hi, I’m ${this.name}`;
  }
}
```

---

## 💡 Pro Tips for Interviews

* Use `interface` for shape and `type` for unions/intersections.
* Generics improve reusability.
* `unknown` is safer than `any`.
* `never` is used for unreachable code.
* TypeScript does static type-checking, not runtime validation.


# SQL Cheat Sheet – Interview Quick Reference

## ✅ Basic SQL Syntax

```sql
SELECT column1, column2 FROM table;
INSERT INTO table (col1, col2) VALUES (val1, val2);
UPDATE table SET col1 = val1 WHERE condition;
DELETE FROM table WHERE condition;
```

---

## ✅ Clauses & Keywords

```sql
WHERE       -- filter rows
GROUP BY    -- group rows for aggregate functions
ORDER BY    -- sort results
HAVING      -- filter after GROUP BY
LIMIT       -- restrict number of rows (MySQL/Postgres)
```

---

## ✅ Joins

```sql
-- INNER JOIN
SELECT * FROM A INNER JOIN B ON A.id = B.a_id;

-- LEFT JOIN
SELECT * FROM A LEFT JOIN B ON A.id = B.a_id;

-- RIGHT JOIN
SELECT * FROM A RIGHT JOIN B ON A.id = B.a_id;

-- FULL OUTER JOIN (Not in MySQL directly)
SELECT * FROM A FULL OUTER JOIN B ON A.id = B.a_id;
```

---

## ✅ Aggregate Functions

```sql
COUNT(*)     -- number of rows
SUM(column)  -- total value
AVG(column)  -- average value
MAX(column)  -- highest value
MIN(column)  -- lowest value
```

---

## ✅ Common Interview Queries

### 1. Get top 5 highest paid employees

```sql
SELECT name, salary FROM employees ORDER BY salary DESC LIMIT 5;
```

### 2. Find duplicate rows

```sql
SELECT col, COUNT(*) FROM table GROUP BY col HAVING COUNT(*) > 1;
```

### 3. Get department-wise employee count

```sql
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

### 4. Fetch 2nd highest salary

```sql
SELECT MAX(salary) FROM employees WHERE salary < (SELECT MAX(salary) FROM employees);
```

### 5. Get employees who don't belong to any department

```sql
SELECT * FROM employees WHERE department_id IS NULL;
```

---

## ✅ Constraints

```sql
PRIMARY KEY   -- unique + not null
FOREIGN KEY   -- reference another table
UNIQUE        -- column must have unique values
NOT NULL      -- disallow nulls
CHECK         -- enforce condition
DEFAULT       -- assign default value
```

---

## 💡 Pro Tips for Interviews

* Always pair `GROUP BY` with aggregate functions.
* Use `HAVING` to filter grouped data.
* Know difference between `WHERE` (rows) and `HAVING` (groups).
* Explain NULL-safe comparisons: `IS NULL`, `IS NOT NULL`.
* Understand when to use subqueries vs joins.
