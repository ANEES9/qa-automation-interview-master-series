# Q028. What is the difference between throw and throws in Java?

## Interview Answer

`throw` is used inside a method to explicitly throw an exception.

`throws` is used in a method declaration to tell callers that the method may throw an exception. In automation frameworks, `throw` is used to fail fast with meaningful messages, while `throws` is common when calling checked-exception APIs.

---

## Detailed Explanation

`throw` and `throws` are related to exception handling, but they are used in different places.

| Feature | throw | throws |
| --- | --- | --- |
| Used where | Inside method body | Method declaration |
| Purpose | Actually throws exception | Declares possible exception |
| Followed by | Exception object | Exception class name |
| Count | One exception object at a time | Multiple exception types possible |
| Example | `throw new IllegalStateException()` | `throws IOException` |

In framework code, `throw` helps create clear failures when configuration or test data is invalid.

---

## Why Interviewers Ask This

Interviewers ask this to verify that you understand exception syntax and responsibility.

They also check whether you can write clear framework errors instead of letting failures appear as confusing null pointer or file errors.

---

## Real Project Example

If a browser name from configuration is invalid, the driver factory should throw an exception with a clear message like `Unsupported browser: safari`.

This is better than returning `null` and causing a later `NullPointerException`.

---

## Java Code Example

```java
public class BrowserValidator {
    public void validateBrowser(String browserName) {
        if (browserName == null || browserName.isBlank()) {
            throw new IllegalArgumentException("Browser name must not be blank");
        }

        if (!browserName.matches("chrome|firefox|edge")) {
            throw new IllegalArgumentException("Unsupported browser: " + browserName);
        }
    }
}
```

---

## Code Explanation

- `throw` explicitly creates and raises an exception.
- `IllegalArgumentException` is used because the input value is invalid.
- The message tells exactly what is wrong.
- This style helps automation failures fail early and clearly.

---

## Best Practices

- Use `throw` for invalid framework state or invalid input.
- Use clear exception messages.
- Use `throws` for checked exceptions when the caller should decide handling.
- Avoid declaring `throws Exception` unless absolutely required.
- Do not return `null` for serious setup failures.

---

## Common Mistakes

- Using `throws` inside a method body.
- Using `throw` in the method declaration.
- Throwing generic `Exception` without context.
- Returning `null` instead of failing fast.
- Declaring checked exceptions that never occur.

---

## Follow-up Questions

- Can we throw unchecked exceptions?
- Can one method declare multiple exceptions using `throws`?
- What happens after `throw` executes?
- What is a custom exception?
- Should a driver factory return `null` for an unsupported browser?
- What is the difference between `throw`, `throws`, and `try-catch`?

---

## Summary

- `throw` throws an exception object.
- `throws` declares possible exceptions.
- `throw` is used inside a method.
- `throws` is used in a method signature.
- Automation frameworks use `throw` for clear setup failures.

---

## Quick Revision

- `throw new ExceptionType()`.
- `method() throws IOException`.
- `throw` executes.
- `throws` declares.
- Use meaningful messages.

---

## Interview Tip

Give a driver factory validation example. It shows that you use exceptions to improve framework quality, not only to answer syntax questions.

---

## Difficulty

Beginner to Intermediate

---

## Experience Level

Suitable for Freshers, 2 Years, and 3-5 Years.

---

## Related Questions

- Q026
- Q027
- Q029

