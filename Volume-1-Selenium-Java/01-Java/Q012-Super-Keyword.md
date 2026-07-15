# Q012. What is the super keyword in Java?

## Interview Answer

The `super` keyword refers to the immediate parent class object.

It is used to access parent class variables, call parent class methods, and call the parent class constructor. In automation frameworks, `super` is useful when child test classes or page classes need behavior from a base class.

---

## Detailed Explanation

`super` helps a child class reuse or extend parent class behavior.

Common uses:

- `super.variableName` to access a parent variable.
- `super.methodName()` to call a parent method.
- `super()` to call a parent constructor.

If a child class constructor does not explicitly call `super(...)`, Java inserts a call to the parent no-argument constructor automatically.

In framework design, base classes often contain setup, teardown, logging, wait utilities, or common page behavior. Child classes can call parent behavior using `super`.

---

## Why Interviewers Ask This

Interviewers ask this to check your understanding of inheritance and constructor flow.

For Selenium automation, they may expect you to explain how child test classes reuse setup methods from a base test class.

---

## Real Project Example

A `BasePage` class may store WebDriver and common methods. A `LoginPage` class can extend `BasePage` and call `super(driver)` to initialize the parent class driver field.

This avoids repeating driver initialization logic in every page class.

---

## Java Code Example

```java
import org.openqa.selenium.WebDriver;

class BasePage {
    protected final WebDriver driver;

    public BasePage(WebDriver driver) {
        this.driver = driver;
    }

    public String getTitle() {
        return driver.getTitle();
    }
}

public class LoginPage extends BasePage {
    public LoginPage(WebDriver driver) {
        super(driver);
    }
}
```

---

## Best Practices

- Use `super()` to initialize parent class dependencies.
- Call `super.methodName()` when parent behavior should be preserved.
- Keep base classes focused and reusable.
- Avoid deep inheritance chains.
- Prefer composition when inheritance does not represent a clear relationship.
- Make parent fields `protected` only when child classes truly need direct access.

---

## Common Mistakes

- Confusing `super` with `this`.
- Forgetting that `super()` must be the first statement in a constructor.
- Trying to access private parent members directly.
- Creating unnecessary inheritance only to reuse one method.
- Overriding a method and forgetting required parent behavior.
- Building very large base test classes.

---

## Follow-up Questions

- What is the difference between `this` and `super`?
- Can `super()` and `this()` be used together in one constructor?
- What happens if a parent class has no default constructor?
- Can `super` access private members?
- Why do child page classes call `super(driver)`?
- What is constructor chaining?

---

## Summary

- `super` refers to the immediate parent class.
- It is used for parent variables, methods, and constructors.
- `super()` must be the first constructor statement.
- Selenium frameworks use `super` in base page and base test designs.
