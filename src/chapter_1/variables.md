# Variables

Variables are names that represent values in the program. They can be declared with the `auto` keyword.

```cpp
int main() {
    auto x = 1; // Creates a variable called x with the value 1
    std::cout << x << '\n';
    x = 2; // Uses the = operator to reassign to the value 2
    std::cout << x << '\n';
}
```

Note that by default, variables are mutable in C++. We can declare a variable to be immutable or read-only with the `const` keyword. With this, the compiler will prevent us from modifying the variable.

```cpp
int main() {
    const auto x = 1; // Creates an immutable variable
    std::cout << x << '\n';
    x = 2; // Compile Time Error
    std::cout << x << '\n';
}
```

When we try to compile this code with clang, we get the following error:

```plaintext
<source>: In function 'int main()':

<source>:6:7: error: assignment of read-only variable 'x'

    6 |     x = 2;
      |     ~~^~~
```

This is a helpful error. It shows exactly the line number where the problem is, as well as an easily understandable description of why the error occurred.

It is a good idea to always use `const` by default, and only remove it as needed. This prevents bugs that come from accidental modification of variables when it is not wanted. You may think "Come on guy, I don't need const to know I won't modify it. I just won't do it.". Believe me, there are situations where accidental mutations come much easier than you would think.

## Scope

All variables (and as a matter of fact, all names) in C++ have scope. Scope is simply in what context a given variable is visible or not. We can demonstrate this using a block statement, which introduces a new block.

```cpp
    const int x = 3;
    { // new block
        const int y = 4;
        // y goes out of scope here
    }
    std::cout << x << '\n';
    std::cout << y << '\n'; // Compile Time Error: y is out of scope
```

Variables can also be global, meaning accessible to every point in the function. However, you should only use this if the variable is immutable; global mutable variables make the logic of the program extremely convoluted and hard to debug, and there is always a better way to solve the problem.

## Immutability vs Constancy

C++ also has compile time constants. These can be declared with the `constexpr` keyword (Constant Expression).

```cpp
    constexpr auto x = 1;
```

These are immutable, like const variables. This may lead you to think that `const` and `constexpr` have the same meaning, but this is not true. You can create an immutable variable whose value isn't known at compile time.

## Static Typing

C++ is a statically typed, strongly typed language. This means that every variable has a type, and that type can't be changed. We are going to be taking a look at various primitive data types in the next section.
