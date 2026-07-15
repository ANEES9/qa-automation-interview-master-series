# Q013. What are access modifiers in Java?

## Interview Answer

Access modifiers control the visibility of classes, methods, constructors, and variables.

Java has four access levels: `public`, `protected`, default, and `private`. They help enforce encapsulation and control how different parts of a framework interact with each other.

---

## Detailed Explanation

Access modifiers define where a member can be accessed:

- **public**: Accessible from anywhere.
- **protected**: Accessible within the same package and by child classes.
- **default**: Accessible only within the same package. No keyword is used.
- **private**: Accessible only within the same class.

Access control is important for clean framework design. For example, page locators can be private, page actions can be public, and reusable base methods can be protected.

Top-level classes can be `public` or default. They cannot be `private` or `protected`.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you can design maintainable Java classes instead of exposing everything publicly.

For automation engineers, access modifiers are important in page object model, utility classes, framework configuration, and test base classes.

---

## Real Project Example

In a `LoginPage` class, locators should be private because test classes should not directly depend on locator details. Public methods like `loginAs()` should expose meaningful business actions.

This keeps tests readable and reduces maintenance when locators change.

---

## Java Code Example

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class LoginPage {
    private final WebDriver driver;
    private final By usernameInput = By.id("username");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String username) {
        driver.findElement(usernameInput).sendKeys(username);
    }
}
```

---

## Best Practices

- Keep fields private whenever possible.
- Expose behavior through public methods.
- Use protected only for members designed for subclasses.
- Avoid making locators public in page object classes.
- Use default access for package-level helpers when suitable.
- Do not expose framework internals without a reason.

---

## Common Mistakes

- Making all variables public.
- Using protected as a replacement for private.
- Not understanding default access.
- Exposing page locators directly to test classes.
- Making utility constructors public when objects should not be created.
- Confusing access modifiers with non-access modifiers like static and final.

---

## Follow-up Questions

- What is default access in Java?
- Can a top-level class be private?
- What is the difference between protected and default?
- Why should fields be private?
- How do access modifiers support encapsulation?
- Which access modifier is best for Selenium locators?

---

## Summary

- Access modifiers control visibility.
- Java access levels are public, protected, default, and private.
- Private supports encapsulation.
- Page object fields are usually private.
- Public methods should expose meaningful actions.
