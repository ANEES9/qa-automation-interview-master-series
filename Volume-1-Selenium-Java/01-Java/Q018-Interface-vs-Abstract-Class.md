# Q018. What is the difference between interface and abstract class in Java?

## Interview Answer

An interface defines a contract that classes agree to implement. An abstract class can define both common behavior and incomplete behavior for child classes.

Use an interface when you want to define capabilities across unrelated classes. Use an abstract class when classes share a common base, state, or reusable behavior.

---

## Detailed Explanation

An interface can contain abstract methods, default methods, static methods, private helper methods, and constants. A class can implement multiple interfaces.

An abstract class can contain abstract methods, concrete methods, constructors, instance variables, and static members. A class can extend only one abstract class.

Key differences:

- A class can implement multiple interfaces.
- A class can extend only one abstract class.
- Interfaces are best for contracts.
- Abstract classes are best for shared base behavior.
- Abstract classes can hold instance state.
- Interfaces help reduce tight coupling.

---

## Why Interviewers Ask This

Interviewers ask this because many automation frameworks use both concepts.

For Selenium engineers, this question checks whether you can choose the right design for driver factories, report loggers, base pages, and test setup classes.

---

## Real Project Example

A `ReportLogger` interface can have implementations for Allure and Extent Reports.

A `BasePage` abstract class can hold WebDriver, waits, and common page methods. Specific page classes like `LoginPage` and `DashboardPage` can extend it.

---

## Java Code Example

```java
interface ScreenshotTaker {
    void takeScreenshot(String fileName);
}

abstract class BasePage {
    protected final String pageName;

    protected BasePage(String pageName) {
        this.pageName = pageName;
    }

    public String getPageName() {
        return pageName;
    }
}

class LoginPage extends BasePage implements ScreenshotTaker {
    LoginPage() {
        super("Login");
    }

    public void takeScreenshot(String fileName) {
        System.out.println("Save screenshot: " + fileName);
    }
}
```

---

## Best Practices

- Use interfaces for replaceable behavior.
- Use abstract classes for shared state and common logic.
- Avoid forcing unrelated classes into the same abstract base class.
- Keep interfaces small and focused.
- Prefer composition with interfaces for flexible framework design.
- Do not use abstract classes only to prevent object creation.

---

## Common Mistakes

- Saying interfaces cannot have implemented methods in modern Java.
- Saying abstract classes cannot have constructors.
- Using abstract classes when an interface is enough.
- Creating large interfaces with unrelated methods.
- Forgetting a class can implement multiple interfaces.
- Confusing `extends` and `implements`.

---

## Follow-up Questions

- Can an interface have default methods?
- Can an abstract class have a constructor?
- Can a class implement multiple interfaces?
- When would you use an interface in Selenium framework?
- When would you use an abstract class?
- What is multiple inheritance in Java?

---

## Summary

- Interfaces define contracts.
- Abstract classes provide shared base behavior and state.
- A class can implement multiple interfaces.
- A class can extend only one class.
- Selenium frameworks commonly use interfaces for reports and abstract classes for base pages.
