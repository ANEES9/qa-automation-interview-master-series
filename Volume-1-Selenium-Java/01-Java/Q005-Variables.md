# Q005. What are variables in Java?

## Interview Answer

A variable in Java is a named memory location used to store data during program execution. Every variable has a data type, a name, and a value.

In Java, variables are mainly classified as local variables, instance variables, and static variables. In Selenium automation, variables are used to store browser names, URLs, timeouts, test data, page objects, and WebDriver references.

---

## Detailed Explanation

Variables allow Java programs to store and reuse values. Since Java is strongly typed, we must declare the type of data a variable can hold.

Main types of variables:

- **Local variable**: Declared inside a method, constructor, or block.
- **Instance variable**: Declared inside a class but outside methods. Each object gets its own copy.
- **Static variable**: Declared with the `static` keyword. It belongs to the class and is shared across objects.

Example:

```java
String browser = "chrome";
int timeout = 10;
boolean isLoggedIn = true;
```

From Java 10 onward, `var` can be used for local variable type inference. However, in automation code, explicit types are often clearer for readability.

---

## Why Interviewers Ask This

Interviewers ask this because variables are the foundation of Java programming.

For QA automation engineers, they also want to see whether you understand where to keep test data, configuration values, driver objects, and reusable page-level state.

---

## Real Project Example

In a Selenium framework, a local variable can store a search keyword inside a test method. An instance variable can store a page object inside a test class. A static variable can store a common configuration value such as the base application URL.

Using the correct variable type helps avoid shared-state issues during parallel test execution.

---

## Java Code Example

```java
public class LoginTestData {
    static String baseUrl = "https://example.com";
    String username = "qa.user";

    public void printLoginData() {
        String password = "secret";

        System.out.println(baseUrl);
        System.out.println(username);
        System.out.println(password);
    }
}
```

---

## Best Practices

- Use meaningful variable names.
- Keep variable scope as small as possible.
- Avoid unnecessary static variables in test classes.
- Store environment-specific values in configuration files.
- Use `final` for values that should not change.
- Avoid hardcoding sensitive values like passwords.
- Prefer explicit types in shared framework code.

---

## Common Mistakes

- Using unclear names like `x`, `data`, or `temp`.
- Declaring variables as global when local scope is enough.
- Using static WebDriver in parallel execution without proper design.
- Forgetting to initialize local variables before use.
- Storing all test data directly inside test methods.
- Confusing instance variables with local variables.

---

## Follow-up Questions

- What is the difference between local, instance, and static variables?
- What is the default value of an instance variable?
- Can local variables have default values?
- What is the use of `final` with variables?
- What is `var` in Java?
- Why should WebDriver not always be static?

---

## Summary

- Variables store data during program execution.
- Java variables have a type, name, and value.
- Local, instance, and static variables have different scopes.
- Correct variable scope improves framework readability and parallel execution safety.
