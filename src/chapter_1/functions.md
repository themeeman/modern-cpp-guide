# Functions

Functions are fundamental units of code that can be called. You can pass to them parameters, and they can return a single value.

You declare a function by writing its return type, followed by its name, followed by its parameters in brackets. For example,

```cpp
int add(int x, int y) { // Declares a function called add that returns an int, and takes 2 parameters that are ints, x and y.
    return x + y; // The return statement returns a value to the user.
}

int main() {
    const auto result = add(3, 5); // "Calls" the function add with the parameters x=3 and y=5
    std::cout << std::format("The sum of 3 and 5 is {}\n", result); // The result is 8
}
```

