# Java Operations

## Control Structures
- `if-else`
- `while`
- `for`
- `for-each loop`

---

## Reverse an Integer

Steps:
1. Use remainder: `%`
2. Remove the remainder from the number
3. Add the remainder to the result:  
   ```
   result = result * 10 + pop
   ```

### Example

```java
int x = 123, result = 0;
while (x != 0) {
    int pop = x % 10;
    x /= 10;
    result = result * 10 + pop;
}
System.out.println(result); // Output: 321
```

---

## String to Int Conversion

Steps:
1. Skip spaces
2. Check the sign (`+` or `-`)
3. Convert characters to integer:
   - If the character is a number → convert
   - Else → exit the loop and continue from next index

### Notes
- Use `charAt(index)` to get character at a specific index

### Example

```java
String str = "  -42";
int i = 0, result = 0, sign = 1;

// Skip spaces
while (i < str.length() && str.charAt(i) == ' ') i++;

// Check sign
if (i < str.length() && (str.charAt(i) == '+' || str.charAt(i) == '-')) {
    sign = (str.charAt(i) == '-') ? -1 : 1;
    i++;
}

// Convert digits
while (i < str.length() && Character.isDigit(str.charAt(i))) {
    result = result * 10 + (str.charAt(i) - '0');
    i++;
}

result *= sign;
System.out.println(result); // Output: -42
```