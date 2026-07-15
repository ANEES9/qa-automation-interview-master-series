# Q010. What is the final keyword in Java?

## Interview Answer

The `final` keyword is used to restrict modification.

A final variable cannot be reassigned, a final method cannot be overridden, and a final class cannot be inherited. In automation frameworks, `final` is commonly used for constants, fixed configuration values, and mandatory dependencies.

---

## Detailed Explanation

The meaning of `final` depends on where it is used:

- **Final variable**: Value cannot be reassigned after initialization.
- **Final method**: Child classes cannot override it.
- **Final class**: Other classes cannot extend it.

For object references, `final` means the reference cannot point to another object. It does not always mean the object itself is immutable.

Example:

```java
final List<String> browsers = new ArrayList<>();
browsers.add("chrome"); // allowed
// browsers = new ArrayList<>(); // not allowed
```

---

## Why Interviewers Ask This

Interviewers ask this to verify that you understand immutability, inheritance control, and framework design.

For QA automation engineers, `final` is useful when designing page objects, constants, utility classes, and stable framework behavior.

---

## Real Project Example

In a Selenium page class, the `WebDriver` field can be declared as `final` because the page should use the driver passed during construction and should not later point to a different browser session.

This makes the page object safer and easier to understand.

---

## Java Code Example

```java
import org.openqa.selenium.WebDriver;

public class DashboardPage {
    private final WebDriver driver;
    public static final String PAGE_TITLE = "Dashboard";

    public DashboardPage(WebDriver driver) {
        this.driver = driver;
    }

    public final String getExpectedTitle() {
        return PAGE_TITLE;
    }
}
```

---

## Best Practices

- Use `static final` for constants.
- Use `final` for constructor-injected dependencies.
- Use final classes for utility classes when inheritance is not needed.
- Use final methods when behavior must not be changed by subclasses.
- Do not use `final` everywhere without a reason.
- Remember that final references can still point to mutable objects.

---

## Common Mistakes

- Thinking final objects are always immutable.
- Confusing final with finally or finalize.
- Trying to override final methods.
- Trying to extend final classes.
- Leaving final variables uninitialized.
- Using final to hide poor class design.

---

## Follow-up Questions

- What is the difference between final, finally, and finalize?
- Can a final variable be initialized in a constructor?
- Can a final method be overloaded?
- Can a final class have objects?
- Is a final list immutable?
- Why is `String` final in Java?

---

## Summary

- Final restricts reassignment, overriding, or inheritance.
- Final variables cannot be reassigned.
- Final methods cannot be overridden.
- Final classes cannot be extended.
- Final is useful for constants and stable framework dependencies.
