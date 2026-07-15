# Q006. What is method overloading in Java?

## Interview Answer

Method overloading means having multiple methods with the same name in the same class, but with different parameter lists.

The difference can be in the number of parameters, type of parameters, or order of parameters. Method overloading is an example of compile-time polymorphism because the compiler decides which method to call.

---

## Detailed Explanation

Overloading improves readability when several methods perform similar actions with different inputs.

A method can be overloaded by changing:

- Number of parameters.
- Data type of parameters.
- Order of parameters.

A method cannot be overloaded only by changing the return type. Java needs a different parameter list to identify the method call.

In automation frameworks, overloaded methods are useful for reusable actions like clicking, entering text, waiting, taking screenshots, or launching browsers with different options.

---

## Why Interviewers Ask This

Interviewers ask this to check your understanding of polymorphism and method signatures.

For Selenium automation, they may also expect examples from utility classes where the same action supports different input types.

---

## Real Project Example

In a Selenium framework, a `click` utility can be overloaded to click by `WebElement`, by locator, or by locator with a custom timeout.

This makes the utility easy to use while keeping method names consistent.

---

## Java Code Example

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;

public class ElementActions {
    private final WebDriver driver;

    public ElementActions(WebDriver driver) {
        this.driver = driver;
    }

    public void click(WebElement element) {
        element.click();
    }

    public void click(By locator) {
        driver.findElement(locator).click();
    }

    public void click(By locator, int timeoutInSeconds) {
        System.out.println("Wait up to " + timeoutInSeconds + " seconds");
        driver.findElement(locator).click();
    }
}
```

---

## Best Practices

- Overload methods only when they perform the same logical action.
- Keep parameter combinations easy to understand.
- Avoid too many overloads for one method.
- Use clear parameter names.
- Consider builder patterns or options objects when parameters become complex.
- Keep overloaded utility methods consistent across the framework.

---

## Common Mistakes

- Thinking overloading happens in different classes only.
- Saying return type alone can overload a method.
- Creating confusing overloads with similar parameter types.
- Overloading unrelated actions with the same method name.
- Confusing method overloading with method overriding.
- Ignoring compile-time method resolution.

---

## Follow-up Questions

- What is method signature?
- Can we overload the `main` method?
- Can static methods be overloaded?
- Can constructors be overloaded?
- What is compile-time polymorphism?
- What is the difference between overloading and overriding?

---

## Summary

- Method overloading uses the same method name with different parameters.
- It improves readability for similar actions.
- It is resolved at compile time.
- Return type alone is not enough for overloading.
- Selenium utility methods commonly use overloading.
