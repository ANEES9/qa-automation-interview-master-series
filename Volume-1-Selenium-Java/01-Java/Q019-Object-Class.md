# Q019. What is the Object class in Java?

## Interview Answer

`Object` is the root class of all Java classes.

Every class in Java directly or indirectly extends `Object`. Because of this, all Java objects inherit methods such as `toString()`, `equals()`, `hashCode()`, and `getClass()`.

---

## Detailed Explanation

If a class does not explicitly extend another class, Java automatically treats it as a subclass of `Object`.

Important methods from `Object` include:

- `toString()` for string representation.
- `equals()` for object comparison.
- `hashCode()` for hash-based collections.
- `getClass()` for runtime class information.
- `wait()`, `notify()`, and `notifyAll()` for thread communication.

In automation code, overriding `toString()`, `equals()`, and `hashCode()` is useful for test data objects, DTOs, and models used in assertions.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand Java's class hierarchy and common object methods.

For automation engineers, this is useful when comparing expected and actual data, logging test objects, or using objects in collections.

---

## Real Project Example

Suppose we create an `Employee` test data object for validating employee details in an HR application.

If we override `equals()` and `hashCode()`, we can compare expected employee data from an API with actual data from the UI or database more reliably.

---

## Java Code Example

```java
import java.util.Objects;

public class Employee {
    private final String id;
    private final String name;

    public Employee(String id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) {
            return true;
        }
        if (!(obj instanceof Employee other)) {
            return false;
        }
        return Objects.equals(id, other.id) && Objects.equals(name, other.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, name);
    }

    @Override
    public String toString() {
        return "Employee{id='%s', name='%s'}".formatted(id, name);
    }
}
```

---

## Best Practices

- Override `toString()` for useful logging.
- Override `equals()` and `hashCode()` together.
- Use `Objects.equals()` for null-safe comparison.
- Use records for simple immutable data carriers when suitable.
- Avoid using `==` for object value comparison.
- Understand how objects behave in `HashSet` and `HashMap`.

---

## Common Mistakes

- Forgetting that every class extends `Object`.
- Overriding `equals()` but not `hashCode()`.
- Using `==` to compare object values.
- Writing `toString()` with sensitive data like passwords.
- Not understanding why collections need `hashCode()`.
- Confusing object identity with object equality.

---

## Follow-up Questions

- What methods are available in the Object class?
- What is the difference between `==` and `.equals()`?
- Why should `equals()` and `hashCode()` be overridden together?
- What is the use of `toString()`?
- What is object identity?
- How can Java records reduce boilerplate?

---

## Summary

- `Object` is the root class of all Java classes.
- All Java objects inherit methods from `Object`.
- `toString()`, `equals()`, and `hashCode()` are commonly overridden.
- Correct object comparison is important in automation assertions.
