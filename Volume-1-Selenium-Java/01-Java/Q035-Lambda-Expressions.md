# Q035. What are lambda expressions in Java?

## Interview Answer

A lambda expression is a concise way to represent a function or behavior.

Lambdas are mainly used with functional interfaces, streams, and callbacks. In automation code, lambdas are useful for filtering collections, processing test data, custom waits, and writing cleaner utility logic.

---

## Detailed Explanation

Lambda syntax:

```java
(parameters) -> expression
```

Example:

```java
name -> name.startsWith("Admin")
```

A lambda works with a functional interface, which is an interface with exactly one abstract method.

Common examples:

- `Predicate<T>`
- `Function<T, R>`
- `Consumer<T>`
- `Supplier<T>`

Lambdas make collection processing readable when used carefully. They should not make test logic difficult to debug.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand modern Java and functional-style programming basics.

For QA automation engineers, lambdas are common in stream operations, Selenium waits, retry utilities, and filtering data from UI or API responses.

---

## Real Project Example

After reading employee names from a UI table, a lambda can filter names that belong to a specific department or role.

This keeps validation logic concise without writing long loops for simple filtering.

---

## Java Code Example

```java
import java.util.List;

public class LambdaFilterExample {
    public static void main(String[] args) {
        List<String> employeeNames = List.of("Admin User", "QA Analyst", "HR Manager");

        List<String> adminUsers = employeeNames.stream()
                .filter(name -> name.startsWith("Admin"))
                .toList();

        System.out.println(adminUsers);
    }
}
```

---

## Code Explanation

- `stream()` starts processing the list.
- `filter(...)` accepts a lambda expression.
- `name -> name.startsWith("Admin")` returns `true` for matching names.
- `toList()` collects the filtered result into a list.

---

## Best Practices

- Use lambdas for simple, readable behavior.
- Keep lambda expressions short.
- Use method references when they improve readability.
- Avoid complex assertions hidden inside lambdas.
- Prefer normal methods when logic needs debugging or reuse.
- Use streams carefully with Selenium elements because the DOM can change.

---

## Common Mistakes

- Using lambdas without understanding functional interfaces.
- Writing long multi-line lambdas that reduce readability.
- Overusing streams in simple test steps.
- Ignoring stale element risks when processing Selenium elements lazily.
- Thinking lambdas replace all methods or loops.

---

## Follow-up Questions

- What is a functional interface?
- What is the difference between lambda and anonymous class?
- What is a method reference?
- What is `Predicate`?
- How are lambdas used with streams?
- Can lambdas make Selenium code harder to debug?

---

## Summary

- Lambdas provide concise behavior.
- They work with functional interfaces.
- They are useful with streams and collection filtering.
- Automation code should use lambdas when they improve readability.

---

## Quick Revision

- Syntax: `(input) -> result`.
- Needs functional interface.
- Common with streams.
- Keep lambdas short.
- Use carefully in Selenium code.

---

## Interview Tip

Use a `List<String>` filtering example first, then mention Selenium waits or UI data validation as practical applications.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 3-5 Years.

---

## Related Questions

- Q022
- Q023
- Q033

