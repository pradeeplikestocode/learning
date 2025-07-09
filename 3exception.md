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
