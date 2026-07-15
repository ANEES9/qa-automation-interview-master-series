# Q025. What is the difference between HashMap and Hashtable in Java?

## Interview Answer

`HashMap` and `Hashtable` both store key-value pairs, but `HashMap` is not synchronized and allows one `null` key, while `Hashtable` is synchronized and does not allow `null` keys or values.

In modern Java automation projects, `HashMap` is preferred. `Hashtable` is legacy and is rarely used in new framework code.

---

## Detailed Explanation

`HashMap` is part of the Java Collections Framework and is widely used for fast key-based lookup.

`Hashtable` is an older synchronized class. Synchronization makes individual operations thread-safe, but it also adds overhead. For modern concurrent use cases, `ConcurrentHashMap` is usually preferred over `Hashtable`.

| Feature | HashMap | Hashtable |
| --- | --- | --- |
| Introduced | Java 1.2 collections | Legacy class |
| Synchronization | Not synchronized | Synchronized |
| Null key | Allows one | Not allowed |
| Null values | Allows multiple | Not allowed |
| Performance | Usually faster | Usually slower |
| Modern use | Preferred | Rare |

---

## Why Interviewers Ask This

Interviewers ask this to test collection knowledge, legacy awareness, and thread-safety understanding.

For automation engineers, this also checks whether you can choose the right map for test data, configuration, and parallel execution.

---

## Real Project Example

A Selenium framework can use `HashMap<String, String>` to store test data for a login scenario, such as username, password, role, and expected dashboard title.

For shared data accessed by multiple parallel threads, we should not simply switch to `Hashtable`; we should review the design and consider `ConcurrentHashMap` if shared mutable data is truly needed.

---

## Java Code Example

```java
import java.util.HashMap;
import java.util.Map;

public class LoginDataMapExample {
    public static void main(String[] args) {
        Map<String, String> loginData = new HashMap<>();
        loginData.put("username", "qa.admin");
        loginData.put("password", "securePassword");
        loginData.put("role", "Admin");

        String username = loginData.get("username");
        String role = loginData.getOrDefault("role", "Employee");

        System.out.println(username + " logs in as " + role);
    }
}
```

---

## Code Explanation

- `Map<String, String>` keeps the code dependent on the interface.
- `HashMap` stores login data by key.
- `get()` retrieves a value by key.
- `getOrDefault()` handles missing optional values safely.

---

## Best Practices

- Use `HashMap` for normal key-value test data.
- Use `Map` as the reference type.
- Use `LinkedHashMap` when insertion order matters.
- Use `ConcurrentHashMap` for real concurrent map updates.
- Avoid `Hashtable` in new code unless maintaining legacy code.
- Do not store passwords in logs or reports.

---

## Common Mistakes

- Saying `HashMap` is thread-safe.
- Saying `Hashtable` is preferred for all parallel tests.
- Forgetting that `HashMap` allows one `null` key.
- Using `Map` for complex objects instead of creating a model class.
- Expecting `HashMap` to preserve insertion order.

---

## Follow-up Questions

- What is hashing?
- Can `HashMap` have duplicate keys?
- What happens when we put the same key again?
- What is `ConcurrentHashMap`?
- What is the difference between `HashMap` and `LinkedHashMap`?
- Why is `Hashtable` considered legacy?

---

## Summary

- `HashMap` is modern and commonly used.
- `Hashtable` is synchronized and legacy.
- `HashMap` allows one null key and multiple null values.
- Use `ConcurrentHashMap` for concurrent map use cases.

---

## Quick Revision

- HashMap: not synchronized.
- Hashtable: synchronized.
- HashMap allows nulls.
- Hashtable does not allow nulls.
- Prefer HashMap in automation framework code.

---

## Interview Tip

Do not say `Hashtable` is better because it is synchronized. A stronger answer mentions `ConcurrentHashMap` for modern concurrent needs.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 3-5 Years.

---

## Related Questions

- Q022
- Q023
- Q030

