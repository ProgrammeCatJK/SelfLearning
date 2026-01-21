# Integer Cache in Java

## Difference between `new Integer()` and `Integer.valueOf()`

- **`new Integer(18)`** → creates a **new instance** every time  
- **`Integer.valueOf(18)`** → refers to a **cached instance** if the value is within a certain range  

### Examples

```java
// Using new
Integer x = new Integer(18);
Integer y = new Integer(18);
System.out.println(x == y); // false, different instances
```

```java
// Using valueOf within cache range
Integer x = Integer.valueOf(18);
Integer y = Integer.valueOf(18);
System.out.println(x == y); // true, same instance
```

```java
// Using valueOf outside cache range
Integer x = Integer.valueOf(300);
Integer y = Integer.valueOf(300);
System.out.println(x == y); // false, new instance created
```

---

## Why this happens

- Java **caches Integer objects** in the range **-128 to 127**  
- If the value is **within this range**, `Integer.valueOf()` **reuses the same object**  
- If the value is **outside this range**, a **new object is created**  

> In other words: common Integer objects are cached within a fixed range; values outside this range will create new instances.