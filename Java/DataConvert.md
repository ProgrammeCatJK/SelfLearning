# Java Data Conversion + Casting

## Automatic Type Conversion
- **Smaller data type → larger data type automatically** during operations

```
byte → short → int → long → float → double
char → int → long → float → double
```

- Happens **during operations** without explicit casting

---

## Explicit Casting
- When converting **larger type → smaller type**, you must cast manually:

```java
(Type) (value / operation)
```

### Example

```java
byte b = 50;
b = (byte)(b * 2); // Without casting, this will not compile
```

**Explanation:**
- `b * 2` → `b` promoted to `int` during multiplication
- Result is `int`, cannot assign to `byte` without explicit cast