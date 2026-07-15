# Q007. What is method overriding in Java?

## Interview Answer

Method overriding means a child class provides its own implementation of a method that is already defined in the parent class.

The method name, return type, and parameters must be compatible with the parent method. Overriding is an example of runtime polymorphism because the method call is decided based on the actual object at runtime.

---

## Detailed Explanation

Overriding is used when a subclass wants to change or extend parent class behavior.

Rules for overriding:

- The method must exist in the parent class.
- The child method must have the same method signature.
- The return type must be the same or covariant.
- Access cannot be more restrictive than the parent method.
- Private methods cannot be overridden.
- Static methods are hidden, not overridden.
- Final methods cannot be overridden.

The `@Override` annotation is recommended because it helps the compiler catch mistakes.

---

## Why Interviewers Ask This

Interviewers ask this to check your understanding of inheritance and runtime polymorphism.

In automation, overriding is useful in framework design, especially when different pages, browsers, environments, or test types need customized behavior.

---

## Real Project Example

In a test framework, a base report class may define a `logResult()` method. A child class for UI tests can override it to attach screenshots, while an API test class can override it to attach request and response details.

The test runner can call the same method name, but the actual behavior depends on the object.

---

## Java Code Example

```java
class BaseTest {
    public void afterTest() {
        System.out.println("Close browser and write basic logs");
    }
}

class UiTest extends BaseTest {
    @Override
    public void afterTest() {
        System.out.println("Capture screenshot");
        System.out.println("Close browser and write UI logs");
    }
}

public class OverrideExample {
    public static void main(String[] args) {
        BaseTest test = new UiTest();
        test.afterTest();
    }
}
```

---

## Best Practices

- Always use the `@Override` annotation.
- Keep overridden behavior aligned with the parent contract.
- Avoid changing behavior in a surprising way.
- Use `super.methodName()` when parent behavior should also run.
- Do not overuse inheritance when composition is simpler.
- Keep base classes stable and focused.

---

## Common Mistakes

- Confusing overriding with overloading.
- Reducing method visibility in the child class.
- Trying to override private or final methods.
- Thinking static methods are overridden.
- Forgetting the `@Override` annotation.
- Changing parameters and accidentally overloading instead of overriding.

---

## Follow-up Questions

- What is runtime polymorphism?
- Can static methods be overridden?
- Can private methods be overridden?
- What is a covariant return type?
- What is the use of `super` in overriding?
- What is the difference between overloading and overriding?

---

## Summary

- Method overriding allows a child class to provide specific behavior.
- It requires the same method signature.
- It supports runtime polymorphism.
- `@Override` helps detect mistakes.
- Selenium frameworks use overriding for custom test and page behavior.
