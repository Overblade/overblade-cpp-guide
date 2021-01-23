# Variables

Welcome to the first guide about basic C++ concepts. We'll start rightaway with one of the most important building blocks of programs: **Variables**

## Receiving input

Since we already know the output stream `std::cout`, our goal is now to receive input from the console.
Contrary to `std::cout` there is also `std::cin` ("character input") which can be used to obtain input.

Its syntax is the opposite of cout: It uses `>>` to extract data from it and gets stored in whatever is on the right hand side of it.
Basically,

```cpp
std::cin >> something;
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

Types specify what *kind* of variable you deal with. Consider pets: Pets have a *type* in the sense of what animal one is. A dog is different from a cat and the same
concept applies here.

Depending on what type you use you get different functionality or *operations* you can apply to a variable. Let's look at some basic types:

### Integers

**Integers** are numbers that have no decimal point. Examples would be 1, 20 and 39 but also -7 is an integer. They are not limited to positive numbers. 
A counter example would be 5.9 since we need a decimal point to precisely represent it.

There are various types for integers, but the most well-known is `int` (short for "integer").

```cpp
int myInteger = 4;
```

### Boolean

**Booleans** are named after George Boole who is a pioneer of mathematical logic. The corresponding type is called `bool` which can (contrary to plain integers) hold
only two values: `true` and `false`. This type is usually used to indicate some form of evaluated logical expression. Booleans are used to execute code conditionally.
However, we'll look at its most common usage later.

```cpp
bool myBoolean = true;
```

### Floats

**Float** is an abbreviation for *floating-point number* meaning they don't have a fixed decimal point. The decimal point can *float*.
The reason why computers use floats instead of fixed-point numbers is that floats have a much higher precision close to 0 and less precision the further you strive away from it.
Fixed-point numbers would offer uniform distribution but you rarely have the need for equal precision for big numbers.

The exact representation of floats is beyond the scope of a basic guide. Floating-point numbers utilize complex maths to calculate results with them internally.
Luckily, floats are blazing fast nowadays due to the existence of integrated FPUs (floating-point unit). Care must be taken when working with embedded devices, though.

So, what types do floats use? Simple.

```cpp
float myFloat = 3.14;
```

### Other types

Variations of the aforementioned types exist, however, they are not important for us yet. Together with some other types they form the concept of *fundamental types*.

Fundamental types are basic types which are implemented by the compiler itself and therefore require no standard library header to be included. Their existence is
a *requirement* of the standard.

If you want to learn about the rest of the fundamental types I recommend you to look at the **Types** guide where I explain the difference between each of them.
Don't worry, as soon as we need a new fundamental type I'll walk you through its properties and usages.

Also, as you might have noticed fundamental types are just a subset of all types. Let me tell you one thing: The number of possible types are infinite.
You can create your *own types*. We'll learn later how this is possible.

## Naming convention

Very nice. You learnt what types are and got to know three basic types: `bool`, `int` and `float`.
There's only one step left before you can create your own variable! It needs a *name*.

In general, you can name your variable however you like. Only a few rules restrict your freedom:

- Names can only start with ASCII letters (that is, `a-z` and `A-Z`) and the underscore character `_`
- Names can contain ASCII letters, underscores and numbers
- Keywords cannot be used as names

Regarding rule 3, keywords are words reserved by the C++ language. As of now, you know 4 keywords: `return`, `bool`, `float` and `int`. You can identify them when they are
highlighted by your IDE (or this guide). 

The following definitions would be illegal:

```cpp
int bool;
float 1Float;
```

Contrary, the following definitions would be legal:
 
```cpp
int my_int;
float _1234567890;
```

Always try to give your variables names that reflect their purpose.
Finally, these rules also apply to types but not in 100% of all cases. You'll see when we talk about custom types.

## Receiving input (now with variables)

So finally, we get

```cpp
#include <iostream>

int main(){

	int number;
	
	std::cin >> number;
	std::cout << number << std::endl;

	return 0;

}
```

Run it and you should be prompted to enter something into the console. Enter any number and press "Enter" to end your input. You should get

```
42
42
```

(if you entered 42 for example).

As you can see, passing a variable to cout causes the variable's contents to print. Again, you could chain it with e.g. strings:

```cpp
std::cout << "Received " << number << std::endl;
```

to get

```
42
Received 42
```

instead.

## Conclusion

If you made it here, well done! Understanding variables is fundamental to coding. You will always use them. Always.
So what did we learn?

- `std::cin` can be used to receive input via `>>`
- Variables are placeholders and refer to a location in memory
- Variables consist of a type and a name
- `bool`, `int` and `float`, all of which are fundamental types
- Variable names must conform certain rules

## Exercises

1. Try entering letters when you are prompted for input. What happens?
2. Omit capturing input at all (i.e. remove the line with `std::cin`). What happens now?
3. Modify the program in order to be able to receive floats.

## Next up

In the next guide, we'll be talking about something... *undefined*.
