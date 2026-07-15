# Q002. What is the difference between JDK, JRE, and JVM?

## Interview Answer

JDK, JRE, and JVM are three core parts of the Java ecosystem, and each one has a different purpose.

- **JDK (Java Development Kit)** is used to develop, compile, debug, and run Java applications.
- **JRE (Java Runtime Environment)** provides the environment required to run Java applications.
- **JVM (Java Virtual Machine)** executes Java bytecode and helps make Java platform-independent.

In simple terms:

- **JDK = JRE + development tools**
- **JRE = JVM + core libraries**
- **JVM = executes Java bytecode**

---

## Detailed Explanation

The **JVM** is responsible for running Java bytecode. Java programs do not run directly on Windows, Linux, or macOS. They are compiled into bytecode, and that bytecode is executed by the JVM installed for that operating system.

The **JRE** provides everything needed to run a Java application. It includes the JVM, core Java libraries, and runtime files. It does not include development tools such as the Java compiler.

The **JDK** is the complete package used by developers and automation engineers. It includes the JRE along with tools such as `javac`, `jar`, `javadoc`, and debugging utilities.

Relationship:

```text
JDK
|-- Development tools
|   |-- javac
|   |-- jar
|   |-- javadoc
|
|-- JRE
    |-- JVM
    |-- Core libraries
    |-- Runtime files
```

For Selenium WebDriver automation with Java, we install the JDK because automation projects need to be compiled and executed.

---

## Why Interviewers Ask This

Interviewers ask this question to verify that you understand Java fundamentals instead of only memorizing Selenium WebDriver commands.

For QA automation engineers, this topic is important because Java setup issues are common in real projects. A candidate should be able to explain why the JDK is required for Maven, TestNG, Jenkins, and Selenium WebDriver automation.

---

## Real Project Example

In a Selenium WebDriver framework using Maven and TestNG, the local machine requires the JDK because the test code must be compiled before execution.

In Jenkins, the build job also uses a configured JDK to compile the automation project and run the test suite. If the wrong JDK version is configured, the pipeline may fail during compilation or test execution.

---

## Java Code Example

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello Java");
    }
}
```

Compilation:

```bash
javac HelloWorld.java
```

Execution:

```bash
java HelloWorld
```

Execution flow:

```text
Java source code
        |
      javac
        |
Bytecode (.class)
        |
       JVM
        |
Program output
```

---

## Best Practices

- Install a supported JDK version for automation development.
- Configure the `JAVA_HOME` environment variable correctly.
- Keep the JDK version consistent across local machines and CI environments.
- Use an LTS version of Java for enterprise automation projects when possible.
- Verify the Java version before debugging Selenium or Maven execution issues.

---

## Common Mistakes

- Saying JDK and JRE are the same.
- Saying the JVM compiles Java source code.
- Forgetting that the JDK includes the JRE.
- Confusing bytecode with Java source code.
- Thinking the JRE contains the Java compiler.
- Installing only the JRE for automation framework development.

---

## Follow-up Questions

- Why is Java platform-independent?
- What is bytecode?
- What is the `javac` compiler?
- What is garbage collection?
- What happens when we execute a Java program?
- What is the `JAVA_HOME` environment variable?

---

## Summary

- JDK is used to develop, compile, debug, and run Java applications.
- JRE is used to run Java applications.
- JVM executes Java bytecode.
- JDK contains JRE and development tools.
- JRE contains JVM and runtime libraries.
- Selenium WebDriver automation projects usually require the JDK, not only the JRE.
