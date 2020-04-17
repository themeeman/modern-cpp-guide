# Hello, World

To begin this C++ journey, we are going to look at the classic Hello World program. Regardless of your experience with other languages, this will look pretty foreign, so it is worth-while to go through it.

```cpp
import <iostream>

int main() {
    std::cout << "Hello, World!\n";
}
```

There is quite a lot going on in this snippet, so I will break it down into pieces. First, the import statement at the top allows access to the `<iostream>` "header". Importing these headers grants as access to different parts of the C++ standard library.

## The `main` function

This is the entry point for all C++ programs. We will more look into how to write and use functions later in this chapter.

## Namespace std

It then looks up the `cout` name inside the namespace `std`. A namespace is what it sounds like, a collection of names. Everything in the C++ standard library is contained inside `std`, and therefore must be preceded with `std::`.

> ## Note: The Dangers of `using namespace std;`
>
> Most tutorials, books and educational resources about C++ seem to encourage use of `using namespaces std;` at the top of your code. This allows you to omit writing `std::` before every type, which reduces keystrokes.
>
> ```cpp
> import <iostream>
>
> using namespace std; // No!!!
>
> int main() {
>   cout << "Hello World\n";
> }
> ```
>
> However, in practice this is **not a good idea**. This effectively dumps every single name from their home in `std` into the global scope, and `std` is a *huge* namespace. This will introduce hundreds of names for potential name collision errors, including commonly used names like `max`, `min` and `equal`.
>
> This turns your code into a ticking time bomb, because while it might work just fine for now, importing a header can introduce a bunch of new names, causing collisions and breaking the code in confusing ways.
>
> An alternative to this is to do `using` only on specific names you want to include. However, I am personally not a fan of that style.
>
> ```cpp
> import <iostream>
>
> using std::cout; // Fine, but I don't recommend it
>
> int main() {
>    cout << "Hello World\n";
> }
> ```

