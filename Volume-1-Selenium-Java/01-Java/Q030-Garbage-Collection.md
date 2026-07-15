# Q030. What is garbage collection in Java?

## Interview Answer

Garbage collection is Java's automatic memory management process.

The JVM removes objects from heap memory when they are no longer reachable by the application. This helps reduce manual memory management, but developers still need to avoid memory leaks caused by unnecessary object references, static state, and unclosed resources.

---

## Detailed Explanation

Java objects are created in heap memory. When no live reference can reach an object, it becomes eligible for garbage collection.

Simple view:

```text
Reference exists      -> Object is reachable
No reference exists   -> Object is eligible for GC
```

Garbage collection does not guarantee immediate cleanup. The JVM decides when to run GC based on memory pressure and runtime behavior.

GC handles Java objects, but it does not replace proper cleanup for external resources such as browser sessions, files, streams, and database connections.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand memory basics and object lifecycle.

For automation engineers, this matters when frameworks create many page objects, screenshots, reports, browser sessions, and large test data objects.

---

## Real Project Example

If a Selenium framework stores every screenshot as a byte array in a static list, memory usage can grow during long regression runs.

Even though Java has garbage collection, those objects remain reachable through the static list, so GC cannot remove them.

---

## Java Code Example

```java
import java.util.ArrayList;
import java.util.List;

public class ReportAttachmentStore {
    private final List<String> attachmentPaths = new ArrayList<>();

    public void addAttachmentPath(String filePath) {
        attachmentPaths.add(filePath);
    }

    public void clearAfterTest() {
        attachmentPaths.clear();
    }
}
```

---

## Code Explanation

- The class stores screenshot or report attachment paths.
- `clearAfterTest()` removes references after a test.
- Once references are removed and no other references exist, related objects can become eligible for GC.
- Storing paths is lighter than storing large file content in memory.

---

## Best Practices

- Do not keep unnecessary static references.
- Close external resources explicitly.
- Call `driver.quit()` after test execution.
- Avoid storing large screenshots or API payloads in memory for long runs.
- Use test framework teardown methods to release resources.
- Do not rely on `System.gc()` in framework code.

---

## Common Mistakes

- Thinking garbage collection closes browsers.
- Calling `System.gc()` to fix framework memory problems.
- Keeping WebDriver or test data in static collections.
- Confusing object eligibility with immediate deletion.
- Not closing files, database connections, or browser sessions.

---

## Follow-up Questions

- When is an object eligible for garbage collection?
- Does Java guarantee when GC will run?
- What is heap memory?
- Can static references cause memory leaks?
- Does garbage collection close WebDriver sessions?
- What is the difference between memory cleanup and resource cleanup?

---

## Summary

- Garbage collection removes unreachable objects.
- GC is managed by the JVM.
- GC timing is not guaranteed.
- External resources still need explicit cleanup.
- Static references can prevent cleanup.

---

## Quick Revision

- JVM manages GC.
- Unreachable objects are eligible.
- GC is not immediate.
- Close browser sessions manually.
- Avoid static memory leaks.

---

## Interview Tip

For Selenium interviews, clearly say that GC does not replace `driver.quit()`.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 3-5 Years.

---

## Related Questions

- Q009
- Q026
- Q025

