# Q024. What is the difference between ArrayList and LinkedList in Java?

## Interview Answer

`ArrayList` and `LinkedList` both implement the `List` interface, but their internal storage is different.

`ArrayList` uses a dynamic array, so accessing elements by index is fast. `LinkedList` uses linked nodes, so adding or removing elements from the beginning or middle can be more efficient in some cases. In automation frameworks, `ArrayList` is used more often.

---

## Detailed Explanation

`ArrayList` stores elements in a resizable array. It is efficient for reading data using indexes and for most normal automation use cases.

`LinkedList` stores elements as nodes. Each node points to the next and previous node.

```text
LinkedList
[A] <-> [B] <-> [C]
```

Comparison:

| Feature | ArrayList | LinkedList |
| --- | --- | --- |
| Internal structure | Dynamic array | Doubly linked nodes |
| Random access | Faster | Slower |
| Insert/delete in middle | May require shifting | Node links change |
| Memory usage | Lower | Higher |
| Common automation use | Very common | Less common |

---

## Why Interviewers Ask This

Interviewers ask this to check whether you know that collection implementations matter, not only collection interfaces.

For QA automation, they expect a practical answer: `ArrayList` is usually enough for web elements, test data rows, dropdown values, and API response lists.

---

## Real Project Example

When collecting all values from a dropdown using Selenium, `ArrayList<String>` is a good choice because we usually add values and then read or compare them.

`LinkedList` is rarely needed in UI automation unless we are implementing queue-like processing or frequent insertions/removals.

---

## Java Code Example

```java
import java.util.ArrayList;
import java.util.List;

public class DropdownValuesExample {
    public static void main(String[] args) {
        List<String> actualStatuses = new ArrayList<>();
        actualStatuses.add("Active");
        actualStatuses.add("Inactive");
        actualStatuses.add("Pending");

        List<String> expectedStatuses = List.of("Active", "Inactive", "Pending");

        if (!actualStatuses.equals(expectedStatuses)) {
            throw new AssertionError("Status dropdown values do not match");
        }
    }
}
```

---

## Code Explanation

- The variable type is `List`, so the code depends on the interface.
- `ArrayList` is used as the implementation because it is efficient for normal read-heavy data.
- `List.of()` creates expected fixed test data.
- `.equals()` compares list values and order.

---

## Best Practices

- Prefer `ArrayList` for most automation data.
- Declare variables using the `List` interface.
- Use `LinkedList` only when its behavior is clearly useful.
- Avoid choosing collections based only on theory.
- Keep expected lists immutable when they should not change.

---

## Common Mistakes

- Saying `LinkedList` is always faster.
- Declaring everything as `ArrayList` instead of `List`.
- Ignoring memory overhead of linked nodes.
- Using `LinkedList` for simple Selenium element lists.
- Comparing lists with `==` instead of `.equals()`.

---

## Follow-up Questions

- Which is better for random access?
- Which implementation does Selenium return for `findElements()`?
- Why should we declare `List<String>` instead of `ArrayList<String>`?
- Does `ArrayList` allow duplicates?
- Is `ArrayList` synchronized?
- When would `LinkedList` be useful?

---

## Summary

- `ArrayList` uses a dynamic array.
- `LinkedList` uses linked nodes.
- `ArrayList` is better for most automation use cases.
- Use `List` as the reference type.

---

## Quick Revision

- ArrayList: fast index access.
- LinkedList: node-based.
- ArrayList is common in Selenium.
- Both allow duplicates.
- Both maintain insertion order.

---

## Interview Tip

Say that `ArrayList` is your default choice in automation unless a specific insertion/removal pattern justifies `LinkedList`.

---

## Difficulty

Intermediate

---

## Experience Level

Suitable for 2 Years and 3-5 Years.

---

## Related Questions

- Q022
- Q023
- Q021

