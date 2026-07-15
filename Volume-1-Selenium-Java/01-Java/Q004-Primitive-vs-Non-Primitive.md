# Q004. What is the difference between primitive and non-primitive data types in Java?

## Interview Answer

Primitive data types store simple values directly, such as numbers, characters, and boolean values. Examples are `int`, `double`, `char`, and `boolean`.

Non-primitive data types store references to objects. Examples are `String`, arrays, classes, interfaces, collections, and Selenium objects like `WebDriver` and `WebElement`.

The main difference is that primitives hold actual values, while non-primitives hold references to objects in memory.

---

## Detailed Explanation

Java has eight primitive data types:

- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`
- `char`
- `boolean`

Primitive types are lightweight and have default values when used as instance variables. For example, `int` defaults to `0`, and `boolean` defaults to `false`.

Non-primitive types are created from classes, interfaces, arrays, enums, records, or other object types. They can call methods, hold complex data, and can be `null`.

Examples of non-primitive types:

- `String`
- `WebDriver`
- `WebElement`
- `List<String>`
- `Map<String, String>`
- Custom classes like `LoginPage`

---

## Why Interviewers Ask This

Interviewers ask this to check whether you understand Java memory basics and object references.

In automation frameworks, this matters because you frequently work with primitive values such as timeout seconds and retry counts, and non-primitive objects such as drivers, page objects, lists of elements, and test data models.

---

## Real Project Example

In a Selenium framework, `int timeoutInSeconds = 10` is a primitive value used for wait configuration.

`WebDriver driver` is a non-primitive reference that points to a browser driver object. If `driver` is `null` and we call `driver.get(...)`, Java throws a `NullPointerException`.

---

## Java Code Example

```java
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class DataTypeExample {
    public static void main(String[] args) {
        int timeoutInSeconds = 10;
        boolean isHeadless = false;
        String browserName = "chrome";

        WebDriver driver = new ChromeDriver();
        driver.get("https://example.com");

        System.out.println(browserName);
        System.out.println(timeoutInSeconds);
        System.out.println(isHeadless);

        driver.quit();
    }
}
```

---

## Best Practices

- Use primitive types for simple values such as counts, flags, and numeric configuration.
- Use wrapper classes like `Integer` or `Boolean` when a value can be missing or must be used in collections.
- Check non-primitive references before using them when `null` is possible.
- Use meaningful types instead of storing everything as `String`.
- Prefer collections like `List<WebElement>` when handling multiple elements.

---

## Common Mistakes

- Saying `String` is primitive.
- Forgetting that non-primitive variables can be `null`.
- Comparing object values with `==` instead of `.equals()`.
- Using wrapper classes unnecessarily for simple local values.
- Not understanding why `List<int>` is invalid in Java.
- Confusing default values of local variables and instance variables.

---

## Follow-up Questions

- What are the eight primitive data types in Java?
- Is `String` primitive or non-primitive?
- What is the default value of `boolean`?
- What is autoboxing and unboxing?
- Why can collections store `Integer` but not `int`?
- What is a `NullPointerException`?

---

## Summary

- Primitive types store simple values.
- Non-primitive types store object references.
- Java has eight primitive data types.
- `String`, arrays, collections, `WebDriver`, and custom classes are non-primitive.
- Understanding this difference helps avoid null and comparison issues in automation code.
