# Q017. What is abstraction in Java?

## Interview Answer

Abstraction means hiding implementation details and showing only the required functionality to the user.

In Java, abstraction is achieved using abstract classes and interfaces. In Selenium automation, page object methods like `loginAs()` hide the internal locator and WebDriver steps from test classes.

---

## Detailed Explanation

Abstraction focuses on what an object does, not how it does it.

Java provides abstraction through:

- Abstract classes.
- Interfaces.

An abstract class can have abstract methods and concrete methods. An interface defines a contract that classes can implement. Modern Java interfaces can also have default and static methods.

In automation frameworks, abstraction keeps tests clean. A test should express business flow, while page classes and utilities handle implementation details.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you can design readable and maintainable automation code.

For 3-5 years of experience, they expect examples like page object model, driver factory, report interface, wait utilities, or test data readers.

---

## Real Project Example

A test method can call `loginPage.loginAs("qa.user", "secret")`.

The test does not need to know which locators are used, whether waits are applied, or how the click is performed. That complexity is hidden inside the page class.

---

## Java Code Example

```java
interface ReportLogger {
    void logPass(String message);
    void logFail(String message);
}

class AllureReportLogger implements ReportLogger {
    public void logPass(String message) {
        System.out.println("PASS: " + message);
    }

    public void logFail(String message) {
        System.out.println("FAIL: " + message);
    }
}
```

---

## Best Practices

- Hide implementation details behind meaningful methods.
- Use interfaces for contracts with multiple implementations.
- Use abstract classes when shared state or common behavior is required.
- Keep test methods focused on business scenarios.
- Avoid exposing locators and low-level WebDriver calls in tests.
- Do not create abstractions before there is a clear need.

---

## Common Mistakes

- Confusing abstraction with encapsulation.
- Creating too many interfaces without purpose.
- Making tests depend on low-level implementation details.
- Treating abstraction as only abstract classes.
- Adding abstract layers that make debugging harder.
- Exposing Selenium locators from page classes.

---

## Follow-up Questions

- How is abstraction achieved in Java?
- What is the difference between abstraction and encapsulation?
- What is an abstract class?
- What is an interface?
- How does page object model use abstraction?
- Can an abstract class have a constructor?

---

## Summary

- Abstraction hides implementation details.
- Java supports abstraction using abstract classes and interfaces.
- Page object model is a practical abstraction in Selenium.
- Good abstraction makes tests readable and maintainable.
