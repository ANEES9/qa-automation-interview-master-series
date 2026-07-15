# Q023. What is the difference between List, Set, and Map in Java?

## Interview Answer

`List`, `Set`, and `Map` are used to store groups of data, but they solve different problems.

`List` stores ordered data and allows duplicates. `Set` stores unique values. `Map` stores data as key-value pairs. In automation, we use `List` for web elements, `Set` for unique values, and `Map` for test data or configuration.

---

## Detailed Explanation

These are core parts of the Java Collections Framework.

| Feature | List | Set | Map |
| --- | --- | --- | --- |
| Stores | Values | Unique values | Key-value pairs |
| Duplicates | Allowed | Not allowed | Keys unique, values can duplicate |
| Order | Depends on implementation | Depends on implementation | Depends on implementation |
| Common class | `ArrayList` | `HashSet` | `HashMap` |
| Selenium use | Multiple elements | Unique UI values | Test data by key |

Example choices:

- Use `List<WebElement>` for table rows.
- Use `Set<String>` to validate duplicate-free menu names.
- Use `Map<String, String>` to store login test data.

---

## Why Interviewers Ask This

Interviewers ask this because collection choice affects correctness and performance.

For automation engineers, this question shows whether you can store UI data, API data, and test data in the right structure.

---

## Real Project Example

To validate an employee table, we can read all employee names into a `List<String>`. To check that no employee ID is duplicated, we can store IDs in a `Set<String>`. To pass login data, we can use a `Map<String, String>` with keys like `username` and `password`.

---

## Java Code Example

```java
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Set;

public class CollectionChoiceExample {
    public static void main(String[] args) {
        List<String> menuItems = List.of("Home", "Employees", "Reports");
        Set<String> uniqueEmployeeIds = new HashSet<>(List.of("E101", "E102", "E103"));
        Map<String, String> loginData = new HashMap<>();

        loginData.put("username", "qa.admin");
        loginData.put("password", "securePassword");

        System.out.println(menuItems);
        System.out.println(uniqueEmployeeIds.contains("E101"));
        System.out.println(loginData.get("username"));
    }
}
```

---

## Code Explanation

- `List.of()` creates a fixed list of menu items.
- `HashSet` keeps employee IDs unique.
- `HashMap` stores login data using meaningful keys.
- The example shows three common automation data patterns.

---

## Best Practices

- Use `List` when order or duplicates matter.
- Use `Set` when uniqueness matters.
- Use `Map` for key-value data.
- Choose ordered implementations like `LinkedHashMap` when insertion order matters.
- Avoid using `Map` as a replacement for a proper model class when data becomes complex.

---

## Common Mistakes

- Using `List` and then manually removing duplicates.
- Expecting `HashSet` to preserve insertion order.
- Expecting `HashMap` keys to allow duplicates.
- Using raw types without generics.
- Storing unrelated data in one large map.

---

## Follow-up Questions

- Which collection does Selenium `findElements()` return?
- Can a `Set` contain `null`?
- Can a `Map` have duplicate keys?
- What is the difference between `HashMap` and `LinkedHashMap`?
- When would you use `TreeSet`?
- What is the difference between `List.of()` and `new ArrayList<>()`?

---

## Summary

- `List` stores ordered values and allows duplicates.
- `Set` stores unique values.
- `Map` stores key-value pairs.
- Correct collection choice improves test clarity and correctness.

---

## Quick Revision

- List: ordered values.
- Set: unique values.
- Map: key-value pairs.
- Hash implementations do not guarantee insertion order.
- Selenium `findElements()` returns a list.

---

## Interview Tip

Use a Selenium table example to explain all three. It sounds much stronger than only giving definitions.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 2 Years and 3-5 Years.

---

## Related Questions

- Q022
- Q024
- Q025

