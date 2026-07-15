# Q020. What is the difference between String, StringBuilder, and StringBuffer in Java?

## Interview Answer

`String` is immutable, which means its value cannot be changed after creation.

`StringBuilder` is mutable and not synchronized, so it is faster for single-threaded string modification. `StringBuffer` is also mutable, but its methods are synchronized, so it is thread-safe and usually slower.

In most automation code, use `String` for normal text and `StringBuilder` for repeated string building.

---

## Detailed Explanation

`String` creates immutable text objects. When we modify a string, Java creates a new object instead of changing the existing one.

`StringBuilder` allows modification of the same object. It is useful when building dynamic XPath, log messages, SQL queries for tests, or large reports in a single thread.

`StringBuffer` is similar to `StringBuilder`, but it is synchronized. This makes it safer for shared multi-threaded use, but slower in normal cases.

Comparison:

- `String`: immutable and commonly used.
- `StringBuilder`: mutable, faster, not synchronized.
- `StringBuffer`: mutable, synchronized, thread-safe.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand immutability, memory usage, and performance basics.

For Selenium automation, this matters when creating dynamic locators, test logs, request payloads, or report text.

---

## Real Project Example

If a framework builds a dynamic XPath once, a `String` is fine.

If a utility builds a long report message by appending multiple values, `StringBuilder` is better because it avoids creating many unnecessary intermediate string objects.

---

## Java Code Example

```java
public class StringExample {
    public static void main(String[] args) {
        String fieldName = "username";
        String xpath = "//input[@name='" + fieldName + "']";

        StringBuilder message = new StringBuilder();
        message.append("Locator: ")
                .append(xpath)
                .append(", Status: ")
                .append("visible");

        System.out.println(message);
    }
}
```

---

## Best Practices

- Use `String` for simple and fixed text values.
- Use `StringBuilder` for repeated concatenation inside loops.
- Use `StringBuffer` only when synchronized mutable strings are really required.
- Avoid building complex XPath strings when stable locators are available.
- Do not store passwords or secrets in long-lived strings when avoidable.
- Prefer readable code over premature optimization.

---

## Common Mistakes

- Saying `StringBuilder` is thread-safe.
- Saying `StringBuffer` is always better because it is synchronized.
- Using `String` concatenation heavily inside loops.
- Thinking string immutability means the variable cannot be reassigned.
- Comparing strings with `==` instead of `.equals()`.
- Overusing dynamic XPath instead of better locator strategies.

---

## Follow-up Questions

- Why is `String` immutable?
- What is the string constant pool?
- What is the difference between `==` and `.equals()` for strings?
- When should we use `StringBuilder`?
- Is `StringBuffer` thread-safe?
- How do you build dynamic locators in Selenium?

---

## Summary

- `String` is immutable.
- `StringBuilder` is mutable and faster for single-threaded modifications.
- `StringBuffer` is mutable and synchronized.
- Use `String` for normal text and `StringBuilder` for repeated building.
- Correct string handling improves readability and performance in automation code.
