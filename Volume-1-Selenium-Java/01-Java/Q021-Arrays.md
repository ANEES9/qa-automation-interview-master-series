# Q021. What are arrays in Java?

## Interview Answer

An array in Java is a fixed-size container that stores multiple values of the same data type.

Arrays are useful when we know the number of elements in advance. In automation, arrays can store small fixed sets of browsers, roles, or test inputs. For dynamic data, collections like `List` are usually preferred.

---

## Detailed Explanation

An array stores elements in continuous index-based positions. The first element starts at index `0`.

Basic structure:

```text
Index:   0        1        2
Value: chrome  firefox  edge
```

Important points:

- Arrays have fixed length.
- Arrays can store primitives or objects.
- Array length is accessed using `.length`.
- Invalid indexes throw `ArrayIndexOutOfBoundsException`.
- Arrays are objects in Java.

Arrays are simple and fast, but they are not flexible when data grows or shrinks during execution.

| Feature | Array | Collection |
| --- | --- | --- |
| Size | Fixed | Dynamic |
| Data type | Same type | Same generic type |
| Methods | Limited | Rich API |
| Best use | Small fixed data | Dynamic test data |

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand basic data storage, indexing, fixed size, and common runtime errors.

For QA automation engineers, arrays are often discussed before collections because many test data and locator handling questions build on this concept.

---

## Real Project Example

In a Selenium smoke suite, we may run the same check on a fixed set of browsers: Chrome, Firefox, and Edge. Since the browser list is small and known, an array is acceptable.

For large data-driven testing from Excel, JSON, or database, a collection is usually better.

---

## Java Code Example

```java
public class BrowserArrayExample {
    public static void main(String[] args) {
        String[] browsers = {"chrome", "firefox", "edge"};

        for (String browser : browsers) {
            System.out.println("Run smoke test on: " + browser);
        }
    }
}
```

---

## Code Explanation

- `String[] browsers` declares an array of strings.
- The array contains three fixed browser names.
- The enhanced `for` loop reads each browser safely without manually handling indexes.
- This style is readable for small fixed automation data.

---

## Best Practices

- Use arrays when the number of values is fixed.
- Use enhanced `for` loops when indexes are not required.
- Check array length before accessing by index.
- Prefer `List` when data needs to grow, shrink, filter, or sort.
- Use meaningful variable names like `supportedBrowsers`.

---

## Common Mistakes

- Accessing an index outside the array length.
- Thinking array size can be changed after creation.
- Using `.size()` instead of `.length`.
- Using arrays for complex dynamic test data.
- Forgetting that array indexing starts from `0`.

---

## Follow-up Questions

- What is the default value of an array element?
- What is the difference between array and `ArrayList`?
- Can arrays store objects?
- What is a multidimensional array?
- What exception is thrown for an invalid array index?
- Is array length fixed in Java?

---

## Summary

- Arrays store multiple values of the same type.
- Arrays have fixed length.
- Array indexing starts from `0`.
- Use arrays for small fixed data.
- Use collections for dynamic automation data.

---

## Quick Revision

- Fixed size.
- Same data type.
- Uses `.length`.
- Index starts at `0`.
- Invalid index causes `ArrayIndexOutOfBoundsException`.

---

## Interview Tip

Mention arrays as simple and fast, but explain that collections are preferred for most real automation framework data.

---

## Difficulty

Beginner

---

## Experience Level

Suitable for Freshers, 2 Years, and 3-5 Years.

---

## Related Questions

- Q004
- Q022
- Q023

