# Q009. What is the static keyword in Java?

## Interview Answer

The `static` keyword means a member belongs to the class, not to a specific object.

We can use `static` with variables, methods, blocks, and nested classes. Static members can be accessed using the class name. In automation frameworks, static is useful for constants and utility methods, but it should be used carefully for shared state like WebDriver.

---

## Detailed Explanation

When a variable or method is static, Java creates one shared copy at the class level.

Common uses:

- Static variables for shared values.
- Static methods for utility operations.
- Static blocks for one-time class initialization.
- Static final constants for fixed values.

Example:

```java
public static final int DEFAULT_TIMEOUT = 10;
```

Static methods cannot directly access non-static instance variables because instance variables belong to objects.

In test automation, static misuse can cause serious problems during parallel execution because multiple tests may share and modify the same data.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand class-level memory and shared state.

For Selenium automation, this is important because many candidates make `WebDriver` static without understanding the effect on parallel test execution.

---

## Real Project Example

A framework may define `public static final String BASE_URL` as a constant because the value is common.

However, making `WebDriver driver` static can be risky when tests run in parallel. One test may close the browser while another test is still using the same static driver reference.

---

## Java Code Example

```java
public class FrameworkConfig {
    public static final int DEFAULT_TIMEOUT_SECONDS = 10;

    public static String buildUrl(String path) {
        return "https://example.com" + path;
    }
}

class TestExample {
    public static void main(String[] args) {
        System.out.println(FrameworkConfig.DEFAULT_TIMEOUT_SECONDS);
        System.out.println(FrameworkConfig.buildUrl("/login"));
    }
}
```

---

## Best Practices

- Use `static final` for constants.
- Use static methods for stateless utility operations.
- Avoid storing test-specific data in static variables.
- Be careful with static WebDriver in parallel execution.
- Access static members using the class name.
- Keep static blocks rare and simple.

---

## Common Mistakes

- Making everything static to avoid object creation.
- Using static WebDriver without thread safety.
- Accessing static members through objects.
- Trying to access instance variables directly from static methods.
- Treating static variables as test data storage.
- Confusing static with final.

---

## Follow-up Questions

- Can a static method access instance variables?
- What is a static block?
- What is the difference between static and final?
- Can constructors be static?
- Why is static WebDriver risky?
- What is class-level memory?

---

## Summary

- Static members belong to the class.
- Static variables have one shared copy.
- Static methods are useful for stateless utilities.
- Static constants are common in frameworks.
- Static shared state must be avoided in parallel Selenium execution.
