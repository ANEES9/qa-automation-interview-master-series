# Q033. What is the var keyword in Java?

## Interview Answer

`var` is used for local variable type inference in Java.

It allows the compiler to infer the variable type from the assigned value. `var` can improve readability in some cases, but it should not be overused in automation code where explicit types make tests easier to understand.

---

## Detailed Explanation

`var` was introduced in Java 10 and is available in Java 21.

Example:

```java
var browserName = "chrome";
```

The compiler treats this as:

```java
String browserName = "chrome";
```

Important rules:

- `var` can be used only for local variables.
- It cannot be used for fields.
- It cannot be used without initialization.
- It is not dynamic typing.
- The type is fixed at compile time.

| Point | var |
| --- | --- |
| Scope | Local variables only |
| Type decision | Compile time |
| Dynamic type | No |
| Requires initializer | Yes |
| Good use | Reducing obvious verbosity |

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand modern Java features and their limits.

For automation engineers, it also shows whether you can use Java 21 features carefully without reducing framework readability.

---

## Real Project Example

In a test utility, `var` can be acceptable when the right-hand side clearly shows the type.

For page objects and shared framework APIs, explicit types are often better because many people read and maintain the code.

---

## Java Code Example

```java
import java.util.List;

public class VarExample {
    public static void main(String[] args) {
        var browsers = List.of("chrome", "firefox", "edge");
        var defaultBrowser = browsers.getFirst();

        System.out.println("Default browser: " + defaultBrowser);
    }
}
```

---

## Code Explanation

- The compiler infers `browsers` as `List<String>`.
- `getFirst()` is available on `List` in modern Java versions.
- The compiler infers `defaultBrowser` as `String`.
- The code remains readable because the assigned values are clear.

---

## Best Practices

- Use `var` only when the inferred type is obvious.
- Avoid `var` in complex Selenium or framework code where explicit type helps.
- Do not use `var` to hide poor variable names.
- Prefer explicit types in public examples and shared APIs.
- Remember that `var` is not JavaScript-style dynamic typing.

---

## Common Mistakes

- Thinking `var` makes Java dynamically typed.
- Trying to use `var` as a class field.
- Declaring `var value;` without initialization.
- Overusing `var` and reducing readability.
- Assuming the variable type can change later.

---

## Follow-up Questions

- Is `var` dynamic typing?
- Can `var` be used for instance variables?
- Can `var` be used without initialization?
- When should we avoid `var`?
- Is `var` available in Java 21?
- Does `var` work with lambda parameters?

---

## Summary

- `var` provides local variable type inference.
- The type is still decided at compile time.
- It works only for local variables.
- Use it carefully when readability improves.

---

## Quick Revision

- Java 10+ feature.
- Local variables only.
- Requires initializer.
- Compile-time type.
- Not dynamic typing.

---

## Interview Tip

Say that you use `var` selectively. Interviewers usually prefer readability over showing off language features.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 3-5 Years.

---

## Related Questions

- Q005
- Q004
- Q032

