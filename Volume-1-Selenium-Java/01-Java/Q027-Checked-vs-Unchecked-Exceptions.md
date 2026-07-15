# Q027. What is the difference between checked and unchecked exceptions in Java?

## Interview Answer

Checked exceptions are checked by the compiler and must be handled or declared using `throws`.

Unchecked exceptions occur at runtime and are not forced by the compiler. They usually indicate programming issues, invalid data, or unexpected runtime conditions. In automation, file reading may throw checked exceptions, while Selenium failures like missing elements are usually unchecked exceptions.

---

## Detailed Explanation

Exception hierarchy:

```text
Throwable
|-- Exception
|   |-- IOException          (checked)
|   |-- RuntimeException     (unchecked)
|       |-- NullPointerException
|       |-- IllegalArgumentException
|-- Error
```

Comparison:

| Feature | Checked Exception | Unchecked Exception |
| --- | --- | --- |
| Checked by compiler | Yes | No |
| Must handle or declare | Yes | No |
| Parent type | `Exception` | `RuntimeException` |
| Example | `IOException` | `NullPointerException` |
| Automation example | File read failure | Missing required object |

---

## Why Interviewers Ask This

Interviewers ask this because exception handling is common in framework development.

They want to know whether you understand compile-time enforcement and runtime failures, especially when working with files, APIs, Selenium, and test data.

---

## Real Project Example

Reading a CSV file for test data can throw `IOException`, which is checked.

Accessing a page object before initializing WebDriver can throw `NullPointerException`, which is unchecked and should be fixed in framework design.

---

## Java Code Example

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class ExceptionTypeExample {
    public static void main(String[] args) throws IOException {
        String data = Files.readString(Path.of("test-data/login.json"));

        if (data.isBlank()) {
            throw new IllegalArgumentException("Login test data must not be blank");
        }
    }
}
```

---

## Code Explanation

- `Files.readString()` can throw checked `IOException`.
- The method declares `throws IOException`.
- `IllegalArgumentException` is unchecked and is thrown when data is invalid.
- Both exception types communicate different failure reasons.

---

## Best Practices

- Handle checked exceptions with clear recovery or framework messages.
- Use unchecked exceptions for invalid framework state or invalid arguments.
- Do not catch unchecked exceptions unless you add useful context.
- Avoid swallowing Selenium runtime exceptions.
- Use custom runtime exceptions for framework-level errors when helpful.

---

## Common Mistakes

- Saying checked exceptions happen at compile time.
- Thinking unchecked exceptions cannot be caught.
- Catching `Throwable`.
- Declaring `throws Exception` everywhere.
- Treating all Selenium exceptions as recoverable.

---

## Follow-up Questions

- Is `IOException` checked or unchecked?
- Is `NullPointerException` checked or unchecked?
- Can unchecked exceptions be caught?
- What is the parent class of checked exceptions?
- Why are Selenium exceptions usually unchecked?
- What is a custom exception?

---

## Summary

- Checked exceptions are enforced by the compiler.
- Unchecked exceptions are runtime exceptions.
- File operations often use checked exceptions.
- Selenium runtime failures are commonly unchecked.

---

## Quick Revision

- Checked: handle or declare.
- Unchecked: compiler does not force handling.
- `IOException` is checked.
- `NullPointerException` is unchecked.
- Do not hide real test failures.

---

## Interview Tip

Avoid saying checked exceptions occur during compilation. The compiler checks handling rules; the exception itself still occurs during execution.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 2 Years and 3-5 Years.

---

## Related Questions

- Q026
- Q028
- Q029

