# Control Flow

In this section we will be learning about the fundamental logical constructs that are used to create the control flow and logic of the program.

## If / Else Statement

The if statement allows conditional execution of some code. It looks like this.

```cpp
if (condition) {
    // code
}
```

If the condition is true, then the code inside the block will run. A simple case is checking the value of a boolean variable.

```cpp
const auto t = true;
const auto f = false;

if (t) {
  n and logical operators.  std::cout << "This will appear!\n";
}

if (f) {
    std::cout << "This will not appear!\n";
}
```

For more complex conditions, we can use the comparison operators

## Comparison Operators

| Operator | Function                                     |
|----------|----------------------------------------------|
| ==       | In `a == b`, a is equal to b                 |
| !=       | In `a != b`, a is not equal to b             |
| <        | In `a < b`, a is less than b                 |
| <=       | In `a <= b`, a is less than or equal to b    |
| >        | In `a > b`, a is greater than b              |
| >=       | In `a >= b`, a is greater than or equal to b |

## Logical Operators

