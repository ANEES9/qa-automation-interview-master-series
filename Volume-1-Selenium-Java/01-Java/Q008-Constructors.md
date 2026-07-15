# Q008. What are constructors in Java?

## Interview Answer

A constructor is a special block in a class that is called when an object is created. It is mainly used to initialize object data.

A constructor has the same name as the class and does not have a return type. Java provides a default constructor if we do not define any constructor.

---

## Detailed Explanation

Constructors help create objects in a valid initial state. They run automatically when we use the `new` keyword.

Types of constructors:

- **Default constructor**: Provided by Java when no constructor is written.
- **No-argument constructor**: Written by the developer without parameters.
- **Parameterized constructor**: Accepts values to initialize the object.

Constructors can be overloaded by using different parameter lists.

In Selenium page object model, constructors are commonly used to pass the `WebDriver` instance from the test class to the page class.

---

## Why Interviewers Ask This

Interviewers ask this because constructors are heavily used in object-oriented framework design.

For automation engineers, they often check whether you know how page objects receive WebDriver and how object initialization works.

---

## Real Project Example

In a login page class, the constructor accepts `WebDriver`. This allows the page class to use the same browser session started by the test.

Without proper constructor initialization, page objects may fail with `NullPointerException`.

---

## Java Code Example

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class LoginPage {
    private final WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }

    public void enterUsername(String username) {
        driver.findElement(By.id("username")).sendKeys(username);
    }
}
```

---

## Best Practices

- Use constructors to initialize required dependencies.
- Keep constructors simple.
- Use `final` fields for mandatory dependencies.
- Avoid heavy logic inside constructors.
- Validate important constructor arguments when needed.
- Use constructor overloading only when it improves readability.
- Pass WebDriver through constructors in page object classes.

---

## Common Mistakes

- Adding a return type to a constructor.
- Forgetting that constructor name must match class name.
- Not initializing required fields.
- Creating page objects without passing WebDriver.
- Putting complex test logic inside constructors.
- Thinking constructors can be inherited.

---

## Follow-up Questions

- What is a default constructor?
- Can constructors be overloaded?
- Can constructors be inherited?
- What is constructor chaining?
- What is the use of `this()`?
- Why do page object classes use constructors?

---

## Summary

- Constructors initialize objects.
- Constructor name must match the class name.
- Constructors do not have a return type.
- Java provides a default constructor only when no constructor is defined.
- Page object classes commonly use constructors to receive WebDriver.
