# Q016. What is polymorphism in Java?

## Interview Answer

Polymorphism means one name or reference can behave in different ways depending on the context.

In Java, polymorphism is mainly of two types: compile-time polymorphism through method overloading and runtime polymorphism through method overriding.

---

## Detailed Explanation

The word polymorphism means many forms.

In compile-time polymorphism, the compiler decides which method to call based on the method parameters. Method overloading is the common example.

In runtime polymorphism, the JVM decides which overridden method to call based on the actual object. Method overriding is the common example.

Polymorphism helps write flexible and extensible code. In automation frameworks, it allows common interfaces or parent references to work with different browser, report, page, or test implementations.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand how Java supports flexible framework design.

For Selenium automation, polymorphism appears in WebDriver itself because `WebDriver driver = new ChromeDriver();` uses a parent interface reference for a specific browser implementation.

---

## Real Project Example

In Selenium, `WebDriver` is an interface. We can assign different browser driver objects to the same reference type:

```java
WebDriver driver = new ChromeDriver();
```

Later, the same framework can use `FirefoxDriver` or `EdgeDriver` without changing most test code.

---

## Java Code Example

```java
interface BrowserLauncher {
    void launch();
}

class ChromeLauncher implements BrowserLauncher {
    public void launch() {
        System.out.println("Launch Chrome");
    }
}

class FirefoxLauncher implements BrowserLauncher {
    public void launch() {
        System.out.println("Launch Firefox");
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        BrowserLauncher launcher = new ChromeLauncher();
        launcher.launch();
    }
}
```

---

## Best Practices

- Program to interfaces when multiple implementations are possible.
- Use method overloading for related actions with different inputs.
- Use overriding when child classes need specific behavior.
- Avoid unnecessary polymorphism for simple code.
- Keep interface methods focused and meaningful.
- Use clear names so behavior is easy to understand.

---

## Common Mistakes

- Explaining polymorphism only as method overloading.
- Confusing compile-time and runtime polymorphism.
- Not connecting polymorphism with WebDriver.
- Creating too many implementations without real need.
- Forgetting that overriding requires inheritance.
- Thinking object type and reference type are always the same.

---

## Follow-up Questions

- What is compile-time polymorphism?
- What is runtime polymorphism?
- How is WebDriver an example of polymorphism?
- What is dynamic method dispatch?
- What is the difference between overloading and overriding?
- Can private methods participate in runtime polymorphism?

---

## Summary

- Polymorphism means many forms.
- Overloading is compile-time polymorphism.
- Overriding is runtime polymorphism.
- WebDriver is a practical Selenium example of polymorphism.
- Polymorphism helps build flexible automation frameworks.
