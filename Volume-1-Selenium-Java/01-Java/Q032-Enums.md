# Q032. What are enums in Java?

## Interview Answer

An enum is a special Java type used to define a fixed set of constants.

Enums improve type safety and readability. In automation frameworks, enums are useful for browser names, environments, user roles, locator strategies, and test execution modes.

---

## Detailed Explanation

An enum is better than plain strings when the allowed values are limited.

Example:

```java
enum Browser {
    CHROME,
    FIREFOX,
    EDGE
}
```

Benefits:

- Prevents invalid values.
- Improves readability.
- Works well with switch expressions.
- Can have fields, constructors, and methods.

Using enums avoids mistakes like `"chorme"` or `"fire fox"` in framework code.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you know type-safe alternatives to string constants.

For 3-5 years of experience, they may expect you to use enums in driver factories, environment selection, and role-based test data.

---

## Real Project Example

A Selenium driver factory can accept a `Browser` enum instead of a free text browser name.

This prevents unsupported browser values from reaching the driver creation logic.

---

## Java Code Example

```java
public enum Browser {
    CHROME("chrome"),
    FIREFOX("firefox"),
    EDGE("edge");

    private final String configValue;

    Browser(String configValue) {
        this.configValue = configValue;
    }

    public String configValue() {
        return configValue;
    }
}
```

---

## Code Explanation

- `Browser` defines only supported browser values.
- Each enum constant stores the value used in configuration.
- The constructor is private by design.
- `configValue()` exposes a readable value when needed.

---

## Best Practices

- Use enums for fixed sets of values.
- Avoid string literals for browser, role, or environment names.
- Keep enum names uppercase.
- Add fields or methods only when they improve clarity.
- Validate external config before converting it to an enum.

---

## Common Mistakes

- Using strings when an enum is safer.
- Comparing enum names with lowercase input directly.
- Adding too much logic inside enums.
- Thinking enum constructors are public.
- Not handling invalid configuration values.

---

## Follow-up Questions

- Can enums have constructors?
- Can enums have methods?
- How do you compare enum values?
- Can enum extend a class?
- How would you use enum in a driver factory?
- What is `Enum.valueOf()`?

---

## Summary

- Enums define fixed constants.
- Enums improve type safety.
- Enums are useful for browser, environment, and role values.
- They reduce string-related mistakes in frameworks.

---

## Quick Revision

- Fixed set of constants.
- Type-safe.
- Constants are usually uppercase.
- Can have fields and methods.
- Useful in driver factories.

---

## Interview Tip

Use browser selection as your enum example. It is simple, practical, and directly related to Selenium automation.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 2 Years and 3-5 Years.

---

## Related Questions

- Q009
- Q028
- Q033

