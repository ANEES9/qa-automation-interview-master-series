# Q029. What is try-catch-finally in Java?

## Interview Answer

`try-catch-finally` is used to handle exceptions and execute cleanup code.

Code that may throw an exception goes inside `try`. Exception handling goes inside `catch`. Cleanup code goes inside `finally`, which normally executes whether an exception occurs or not. For resources, modern Java often prefers try-with-resources.

---

## Detailed Explanation

Basic flow:

```text
try
 |-- risky code
catch
 |-- handle exception
finally
 |-- cleanup
```

The `finally` block is useful for cleanup, but it should not be abused. For resources that implement `AutoCloseable`, try-with-resources is cleaner and safer.

Comparison:

| Feature | finally | try-with-resources |
| --- | --- | --- |
| Purpose | General cleanup | Auto-closing resources |
| Resource close | Manual | Automatic |
| Readability | Good for simple cleanup | Better for files, streams, DB |
| Common modern use | Test cleanup hooks | File and stream handling |

---

## Why Interviewers Ask This

Interviewers ask this because cleanup is important in automation.

They want to know whether you can safely close files, database connections, browser sessions, and other resources without hiding real failures.

---

## Real Project Example

In Selenium, browser cleanup is usually handled in TestNG `@AfterMethod` or framework hooks instead of placing `driver.quit()` in every test's `finally` block.

For reading files or streams, try-with-resources is usually better.

---

## Java Code Example

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.List;

public class CsvReader {
    public List<String> readLines(Path filePath) {
        try {
            return Files.readAllLines(filePath);
        } catch (IOException exception) {
            throw new IllegalStateException("Unable to read CSV file: " + filePath, exception);
        } finally {
            System.out.println("Finished CSV read attempt");
        }
    }
}
```

---

## Code Explanation

- The `try` block reads the file.
- The `catch` block adds a meaningful framework error.
- The `finally` block runs after the read attempt.
- The original exception is preserved as the cause.

---

## Best Practices

- Catch specific exceptions.
- Use `finally` for necessary cleanup.
- Prefer try-with-resources for closeable resources.
- Do not put assertions or business logic in `finally`.
- Avoid returning from `finally`.
- Use TestNG hooks for browser cleanup in test frameworks.

---

## Common Mistakes

- Assuming `finally` never runs when an exception occurs.
- Returning a value from `finally`.
- Closing WebDriver too early in a test.
- Catching exceptions only to print them.
- Using `finally` instead of framework teardown hooks.

---

## Follow-up Questions

- Does `finally` always execute?
- What is try-with-resources?
- Can we have try without catch?
- Can we have multiple catch blocks?
- Where should `driver.quit()` be placed in TestNG?
- Why should we avoid return statements in `finally`?

---

## Summary

- `try` contains risky code.
- `catch` handles exceptions.
- `finally` handles cleanup.
- Try-with-resources is preferred for closeable resources.
- Selenium cleanup is usually handled through test framework hooks.

---

## Quick Revision

- try: risky code.
- catch: handling.
- finally: cleanup.
- Prefer specific catches.
- Avoid return from finally.

---

## Interview Tip

Mention TestNG teardown for WebDriver cleanup. It shows real automation framework thinking.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 2 Years and 3-5 Years.

---

## Related Questions

- Q026
- Q027
- Q028

