# Q014. What is encapsulation in Java?

## Interview Answer

Encapsulation is the process of wrapping data and methods together inside a class and restricting direct access to the data.

In Java, encapsulation is usually achieved by making variables private and providing public methods to access or modify them. In Selenium frameworks, page object model is a practical example of encapsulation.

---

## Detailed Explanation

Encapsulation protects object data from direct external modification. Instead of allowing other classes to directly change fields, we expose controlled methods.

Benefits of encapsulation:

- Better data protection.
- Easier maintenance.
- Clear class responsibilities.
- Reduced dependency on internal implementation.
- Improved framework readability.

In page object model, locators and WebDriver interactions are hidden inside page classes. Test classes call business methods like `loginAs()` instead of directly using locators.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand object-oriented design beyond definitions.

For automation engineers, they expect you to connect encapsulation with page object model, reusable components, and maintainable test scripts.

---

## Real Project Example

If the login button locator changes, only the `LoginPage` class should be updated. Test classes should remain unchanged because they call `loginAs(username, password)`.

This is encapsulation in practice.

---

## Java Code Example

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class LoginPage {
    private final WebDriver driver;
    private final By username = By.id("username");
    private final By password = By.id("password");
    private final By loginButton = By.id("login");

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void loginAs(String user, String pass) {
        driver.findElement(username).sendKeys(user);
        driver.findElement(password).sendKeys(pass);
        driver.findElement(loginButton).click();
    }
}
```

---

## Best Practices

- Keep class fields private.
- Expose clear public methods.
- Hide locator details inside page classes.
- Avoid direct WebDriver usage in test methods when using page objects.
- Validate inputs where needed.
- Keep methods focused on meaningful actions.

---

## Common Mistakes

- Saying encapsulation only means getters and setters.
- Making all page locators public.
- Exposing internal framework objects unnecessarily.
- Putting all actions in one large utility class.
- Using getters and setters without any control or purpose.
- Allowing tests to depend on implementation details.

---

## Follow-up Questions

- How is encapsulation achieved in Java?
- How does page object model use encapsulation?
- What is the difference between abstraction and encapsulation?
- Why should variables be private?
- Are getters and setters always required?
- How does encapsulation improve maintainability?

---

## Summary

- Encapsulation wraps data and behavior inside a class.
- It restricts direct access to internal data.
- Private fields and public methods commonly implement encapsulation.
- Page object model is a strong Selenium example of encapsulation.
