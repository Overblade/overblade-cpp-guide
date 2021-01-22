# Variables

Welcome to the first guide about basic C++ concepts. We'll start rightaway with one of the most important building blocks of programs: **Variables**

## Receiving Input

Since we already know the output stream `std::cout`, our goal is now to receive input from the console.
Contrary to `std::cout` there is also `std::cin` ("console in") which can be used to obtain input.

Its syntax is the opposite of cout: It uses `<<` to extract data from it and gets stored in whatever is on the left hand side of it.
Basically,

```cpp
something << std::cin;
```
But, uh... what is `something`?
We need to find a way to actually *store* what we received. Some kind of placeholder, something that exists in memory, something we can *modify*.

Enter variables.

## Variables

A *variable* is an entity that refers to a location in memory. It basically associates a certain *memory address* with a name. Yes, memory is addressable.
That means we can store an intermediate value in actual memory. Great! Exactly what we need.

Although, how do we create a variable? Easy.

```cpp
Type name;
```

Where `Type` is the variable's type and `name` the name you want to refer to it. Oh, you ask what a *type* is? Good that you ask.

## Types

Types specify what *kind* of variable you deal with.

