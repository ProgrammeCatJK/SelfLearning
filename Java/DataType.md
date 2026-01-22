# Java Data Types

## Primitive Data Types

| Data Type | Default Value | Size / bits |
|-----------|---------------|------------|
| boolean   | false         | -          |
| char      | '\u0000'      | 2          |
| byte      | 0             | 1          |
| short     | 0             | 2          |
| int       | 0             | 4          |
| long      | 0             | 8          |
| float     | 0.0f          | 4          |
| double    | 0.0           | 8          |

> 8 bits = 1 byte  
> 1 binary digit = 1 bit  

**Note:**  
- `double` → 用于精准计算 (used for precise calculations)  

---

## Examples

### Int to Char (ASCII conversion)
```java
int value_int = 65;
char value_char  = (char) value_int;
System.out.println(value_char); // Output: A
```

### Int to Char using radix
```java
int value_int = 6;
char value_char = Character.forDigit(value_int, 10); // radix = 10
System.out.println(value_char); // Output: 6
```

### String to Int
```java
String numberStr = "123";
int number = Integer.parseInt(numberStr);
System.out.println(number); // Output: 123
```