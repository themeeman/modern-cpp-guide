# Strings

Strings are one of the most useful and common data structures in all of programming. They are an arbitrarily long sequence of characters. We use strings to encode data for storage, to send data across networks, and we process strings to retrieve data. As such, it is important that any language has a powerful and efficient string type, and C++ is no exception.

In C++, we manipulate strings using the `std::string` data type. To initialize one, we need to convert to it from a string literal.

```cpp
    auto s = std::string("Hello World");
```

This seems somewhat verbose, so fortunately C++ offers a way to create a `std::string` with a literal. To access this, we need to put `using namespace std::literals;` after our import statements, which introduces all of the standard library provided literals into the current scope, so that they are usable.

```cpp
import <iostream>;
import <string>;

using namespace std::literals;

int main() {
    auto s = "Hello World"s;
    std::cout << s << '\n';
}
```

Strings, like the other types we have seen, are mutable by default. One way to manipulate the string is concatenation with the `+=` operator, which is overloaded for `std::string`. This means that when `+=` is used with `std::string`, it is translated into a function call. We will be looking at how to write our own operator overloads in Chapter 3.

```cpp
    auto s = "Hello"s;
    s += " World"; // Note that we can use normal string literals for the `+=` operator.
    std::cout << s << '\n';
```

We can also make an immutable `std::string` with const, like before. Try compiling the next snippet.

```cpp
    const auto s = "Hello"s;
    s += " World";
    std::cout << s << '\n';
```

The compiler will output something like this.

```plaintext

<source>:8:7: error: no viable overloaded '+='

    s += " World";
    ~ ^  ~~~~~~~~

:1168:7: note: candidate function not viable: 'this' argument has type 'const std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >', but method is not marked const

      operator+=(const basic_string& __str)
      ^
...
```

This error may look somewhat complex at first, as the compiler essentially vomits tons of information at you. However, one of the keys to mastering C++ is learning to extract the most helpful pieces of information from the verbose error messages.

For a start, we are using `std::string`, but the compiler is referring to something called `std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >`. This is because `std::string` is actually an alias for an underlying type in the standard library, which we don't have to worry about thanks to the alias. So, internally replace that complicated type with `std::string`.

The reason the error is *so* massive is that the compiler has to check the argument you passed to `+=` against every single *overload* for the operator. We learnt about overloading back in Chapter 1, and it is everywhere in the standard library. However, all of them say "but method is not marked const", which is the key. We are trying to call method that the compiler knows might modify the string, but we are doing it on a `const` variable, so we get the error.

This may seem a very indirect way of just saying "you can't mutate something that is immutable", but it is important to learn how to grep through the error messages C++ throws at you, which you will see is a theme.

## Passing a `std::string` into a function

We can pass an argument of type `std::string` to a function, like normal.

```cpp
void modify(std::string s) {
    s[0] = 'J';
}

int main() {
    auto s = "Hello World"s;
    modify(s);
    std::cout << s;
}
```

In this example, you may expect the change to be visible outside the function, like in some other programming languages. However, in C++, containers are consistent with primitive data types: passing a container by value copies every element in the container. Therefore, inside the function, we are not modifying the original object; rather, we are modifying the copy, so the change won't be visible outside, and it will print `Hello World`.

