# Q026. What is exception handling in Java?

## Interview Answer

Exception handling is a mechanism to handle runtime problems without abruptly stopping the program.

Java uses `try`, `catch`, `finally`, `throw`, and `throws` for exception handling. In Selenium automation, exception handling is important for browser issues, missing elements, timeouts, file reading, API calls, and reporting failures properly.

---

## Detailed Explanation

An exception is an unwanted event that interrupts normal program flow.

Basic flow:

```text
try block -> exception occurs -> matching catch block -> finally block
```

Java exceptions are mainly:

- Checked exceptions.
- Unchecked exceptions.
- Errors.

In automation, we should not hide failures by catching every exception and continuing. A failed test should fail clearly with a useful message, screenshot, or report entry.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you can write stable automation code and debug failures correctly.

They also want to know whether you understand when to handle an exception and when to let the test fail.

---

## Real Project Example

If a test reads data from a JSON file, file-related exceptions should be handled with a clear framework error.

If Selenium cannot find a mandatory login button, the test should fail instead of silently continuing.

---

## Java Code Example

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

public class TestDataReader {
    public String readFile(Path filePath) {
        try {
            return Files.readString(filePath);
        } catch (IOException exception) {
            throw new IllegalStateException("Unable to read test data file: " + filePath, exception);
        }
    }
}
```

---

## Code Explanation

- `Files.readString()` can throw `IOException`.
- The catch block adds a clear framework-level message.
- The original exception is passed as the cause.
- The method fails fast instead of returning incorrect empty data.

---

## Best Practices

- Catch specific exceptions.
- Preserve the original exception cause.
- Add meaningful error messages.
- Do not use empty catch blocks.
- Let tests fail when mandatory application behavior is broken.
- Capture screenshots or logs in test listeners, not everywhere.

---

## Common Mistakes

- Catching `Exception` everywhere.
- Hiding test failures with only `System.out.println()`.
- Returning fake default values after a serious failure.
- Ignoring the original exception cause.
- Using exception handling as a replacement for explicit waits.

---

## Follow-up Questions

- What is the difference between checked and unchecked exceptions?
- What is the use of `finally`?
- What is the difference between `throw` and `throws`?
- What is `NoSuchElementException` in Selenium?
- Should we catch every Selenium exception?
- What is custom exception handling?

---

## Summary

- Exception handling manages runtime problems.
- Java uses `try`, `catch`, `finally`, `throw`, and `throws`.
- Automation code should fail with clear messages.
- Never hide real test failures.

---

## Quick Revision

- Exception interrupts flow.
- Catch specific exceptions.
- Preserve root cause.
- Avoid empty catch blocks.
- Fail fast for framework errors.

---

## Interview Tip

Explain exception handling from a framework stability angle, not only Java syntax.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 2 Years and 3-5 Years.

---

## Related Questions

- Q027
- Q028
- Q029

