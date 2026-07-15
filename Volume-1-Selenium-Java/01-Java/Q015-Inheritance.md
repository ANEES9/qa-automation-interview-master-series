# Q015. What is inheritance in Java?

## Interview Answer

Inheritance is an object-oriented concept where one class acquires properties and methods from another class.

The parent class is called the superclass, and the child class is called the subclass. In Java, inheritance is implemented using the `extends` keyword.

---

## Detailed Explanation

Inheritance promotes code reuse and supports method overriding. A child class can use parent class methods and can also provide its own implementation when required.

Java supports single inheritance with classes. This means one class can extend only one class. Java does not support multiple inheritance with classes to avoid ambiguity. However, a class can implement multiple interfaces.

In automation frameworks, inheritance is often used for base test classes and base page classes.

Example uses:

- `BaseTest` for browser setup and teardown.
- `BasePage` for common WebDriver methods.
- Specialized page classes extending common page behavior.

---

## Why Interviewers Ask This

Interviewers ask this to check your object-oriented programming understanding and framework design maturity.

For Selenium automation, they want to know whether you can reuse common setup and page behavior without duplicating code everywhere.

---

## Real Project Example

A `BaseTest` class can launch the browser before each test and close it after execution. Test classes like `LoginTest` and `DashboardTest` can extend `BaseTest` and reuse setup logic.

This reduces duplication and keeps test classes focused on test scenarios.

---

## Java Code Example

```java
class BaseTest {
    public void startBrowser() {
        System.out.println("Start browser");
    }

    public void closeBrowser() {
        System.out.println("Close browser");
    }
}

public class LoginTest extends BaseTest {
    public void verifyLogin() {
        startBrowser();
        System.out.println("Verify login");
        closeBrowser();
    }
}
```

---

## Best Practices

- Use inheritance only when there is a clear is-a relationship.
- Keep base classes small and stable.
- Avoid deep inheritance chains.
- Use composition when a has-a relationship is more suitable.
- Do not put unrelated utilities into `BaseTest`.
- Override methods carefully and preserve parent contracts.

---

## Common Mistakes

- Using inheritance only to avoid object creation.
- Creating very large base classes.
- Building deep inheritance chains in test frameworks.
- Forgetting that Java classes support single inheritance only.
- Confusing inheritance with interface implementation.
- Overriding methods without understanding side effects.

---

## Follow-up Questions

- What is the `extends` keyword?
- Does Java support multiple inheritance with classes?
- What is method overriding?
- What is the difference between inheritance and composition?
- Why do frameworks use `BaseTest`?
- What is the difference between superclass and subclass?

---

## Summary

- Inheritance allows a child class to reuse parent class members.
- Java uses the `extends` keyword for class inheritance.
- Java supports single inheritance with classes.
- Selenium frameworks commonly use base test and base page classes.
- Inheritance should be used carefully to avoid rigid design.
