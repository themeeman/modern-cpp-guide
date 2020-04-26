# Primitive Data Types

## Integral types

These types represent integers. The simplest type is the type of the integer literals we have seen already, `int`. It is a signed type, so it can represent positive and negative integers. Its size in bytes is implementation defined, so you should use it when the size of the value isn't important.

There are also fixed size integral types, which you obtain from adding `import <cstdint>` at the top of your program.

| Name            | Range                                       |
|-----------------|---------------------------------------------|
| `std::int8_t`   | -128 to 127                                 |
| `std::int16_t`  | -32768 to 32767                             |
| `std::int32_t`  | -2147483648 to 2147483647                   |
| `std::int64_t`  | -9223372036854775808 to 9223372036854775807 |
| `std::uint8_t`  | 0 to 255                                    |
| `std::uint16_t` | 0 to 65535                                  |
| `std::uint32_t` | 0 to 4294967295                             |
| `std::uint64_t` | 0 to 18446744073709551615                   |

You should use these types when you either need very large numbers, or you don't need to waste space.

In order to use them, you need to convert them from an integer literal, like so `const auto x = std::int16_t(10000);`. Note that when the literal is bigger than 9223372036854775807, you need to append a `u` character to it, so that the compiler knows its definitely unsigned, or else you will get a warning. `const auto y = std::uint64_t(18446744073709551615u)`.

> ## Note: Overflow
>
> When you try to go above or below the valid range of an integral type, integer overflow occurs. For unsigned types, this will cause it to wrap around to the the end.
>
> ```cpp
>   const auto x = uint16_t(65535);
>   std::cout << x + 1; // Prints 0
> ```
>
> However, for signed integers, overflow is *defined by the implementation*. That is, it could do anything. Therefore, don't write programs that rely on signed integer overflow.

## Floating Point Types

Floating point types are used to represent decimals. Floating point literals always contain a decimal point, like `3.5` and `1.01`. The default type of a floating point literal is `double`, so this is a sensible default type to use for floats. There also `float` and `long double`, however they are all have unspecified values, so it is best to stick with `double`

## Char Types

