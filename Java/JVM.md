# Java Basic Understanding

## Union Size
- Size of a union = **largest member of the union (in bytes)**

### Example
```java
Union Student {
    int arr[10]; // 40 bytes
    char x;      // 4 bytes
}
sizeof(Union Student) = 40
```

- **Nested Union** → Union inside a union
- **Benefit of union**: memory efficiency — multiple data types share the same memory (member overlap)
- **Downside**: previous value will be overwritten; only one member can hold a valid value at a time
- **Compared to Struct**: Struct sums up sizes of all members, union does not

---

## Java Concurrency and JVM
- Considered one of the hardest topics in Java

---

## Java Intro
- **Java source code → Bytecode → JVM execution**

### Components
- **JDK (Java Development Kit)** → for development
- **JRE (Java Runtime Environment)** → only for running
- **JVM (Java Virtual Machine)** → environment to run on different systems

---

## Java Compilation and Execution
```
Java source (.java)
        ↓ (javac)
Bytecode (.class)
        ↓ (JVM loads)
Interpreted at first
        ↓
Hot code → JIT compiled → Native machine code
```

- Fast startup due to **interpretation**
- High execution performance due to **JIT compilation** of hot code at runtime
- **Hot code** → code that runs often

---

## Java Execution Steps
1. Java code is compiled to bytecode
2. JVM starts by interpreting the bytecode → fast startup
3. JVM monitors execution at runtime
4. Frequently executed parts (“hot code”) are identified
5. JVM JIT-compiles hot code into optimized machine code
6. Optimized machine code is reused, making execution fast