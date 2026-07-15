# Q031. What are wrapper classes, autoboxing, and unboxing in Java?

## Interview Answer

Wrapper classes convert primitive types into objects.

For example, `int` has wrapper class `Integer`, and `boolean` has wrapper class `Boolean`. Autoboxing automatically converts a primitive to its wrapper object. Unboxing automatically converts a wrapper object back to a primitive.

---

## Detailed Explanation

Collections work with objects, not primitives. That is why wrapper classes are needed.

Examples:

| Primitive | Wrapper Class |
| --- | --- |
| `int` | `Integer` |
| `long` | `Long` |
| `double` | `Double` |
| `boolean` | `Boolean` |
| `char` | `Character` |

Autoboxing:

```java
Integer retryCount = 3;
```

Unboxing:

```java
int retries = retryCount;
```

Wrapper values can be `null`, while primitives cannot. This is important when reading optional configuration values.

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand primitives, objects, collections, and null handling.

In automation frameworks, wrapper classes appear in configuration, JSON parsing, API response models, and data-driven testing.

---

## Real Project Example

A test configuration may store an optional retry count as `Integer`. If the value is missing, it can be `null`, and the framework can apply a default.

Using primitive `int` would default to `0`, which may hide whether the value was missing or intentionally set to zero.

---

## Java Code Example

```java
public class RetryConfig {
    private final Integer configuredRetryCount;

    public RetryConfig(Integer configuredRetryCount) {
        this.configuredRetryCount = configuredRetryCount;
    }

    public int retryCount() {
        return configuredRetryCount == null ? 1 : configuredRetryCount;
    }
}
```

---

## Code Explanation

- `Integer` allows the retry value to be missing.
- The constructor stores the configured value.
- `retryCount()` returns a safe primitive `int`.
- The method applies a default when configuration is absent.

---

## Best Practices

- Use primitives for required simple values.
- Use wrapper classes when null or object behavior is needed.
- Be careful with unboxing nullable wrappers.
- Use generics like `List<Integer>` instead of raw lists.
- Validate configuration values before using them.

---

## Common Mistakes

- Trying to create `List<int>`.
- Unboxing a null wrapper and causing `NullPointerException`.
- Using wrappers everywhere without need.
- Comparing wrapper objects with `==`.
- Forgetting that wrappers are objects.

---

## Follow-up Questions

- Why can collections store `Integer` but not `int`?
- What is autoboxing?
- What is unboxing?
- Can wrapper classes be null?
- What happens when a null `Integer` is unboxed?
- What is the wrapper class for `char`?

---

## Summary

- Wrapper classes represent primitives as objects.
- Autoboxing converts primitive to wrapper.
- Unboxing converts wrapper to primitive.
- Wrappers are useful in collections and optional configuration.
- Null unboxing can cause `NullPointerException`.

---

## Quick Revision

- `int` -> `Integer`.
- `boolean` -> `Boolean`.
- Collections need objects.
- Wrapper can be null.
- Be careful with unboxing.

---

## Interview Tip

Mention `List<Integer>` and null unboxing. These two points usually prove that you understand the concept practically.

---

## Difficulty

Beginner to Intermediate

---

## Experience Level

Suitable for Freshers, 2 Years, and 3-5 Years.

---

## Related Questions

- Q004
- Q021
- Q022

