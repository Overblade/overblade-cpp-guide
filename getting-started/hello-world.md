# The Hello World Program

In the last guide we've seen the Hello World example program. Time to understand how it works!

```cpp
#include <iostream>

int main(){

    std::cout << "Hello World!" << std::endl;
    return 0;
    
}
```

## Include directive

Let's start with the line
```cpp
#include <iostream>
```

As already mentioned, this is a *preprocessor directive*. Each of those directives start with a `#`.

Specifically, this directive is the include directive. It causes a file named `iostream` (note that standard library headers omit an extension) to be included.
Inclusion means, its contents are pasted one-by-one. This allows importing functionality from a different file, which is in this case the standard library's `iostream` file.

`iostream` contains *stream-related* functionality. Basically, console input/output which we need later.

## Main function

```cpp
int main(){
```

Whenever you see `main` you are looking at the most important *function* in your whole program: The **main function**. It's where your whole program starts and therefore
there must always be exactly one global function named `main`. Don't worry if you don't know what functions are yet, we'll cover it later.

## Printing to console

```cpp
std::cout << "Hello World!" << std::endl;
```

Remember when we included `iostream`? This is where we use an *object* named `std::cout` ("character output"). Again, if this sounds cryptic to you, don't worry. 
Objects will be covered later, too.

However, there is going on much more in this single line. `<<` denotes that whatever follows it gets printed to `std::cout`. It basically denotes something on the right
gets put into the console out stream. In this case, it's `"Hello World!"`. 

`"Hello World!"` is what we call a *string*. A string is essentially a sequence of characters or *chars* for short. Putting multiple chars between `""` composes a string
containing these characters. If `std::cout` receives a string, it simply prints it to the console. Easy, isn't it?

The last segment is `std::endl` which is also passed into the stream (as you can see, chaining to `std::cout` is valid). `std::endl` is a special object which causes
to end the current line. Or in more practical terms, it causes the console's cursor to move on to the next line. Also, `std::endl` incurs a *buffer flush*, meaning
the console is updated immediately. Otherwise, the update might be deferred and you won't see the console print immediately.

## Returning from main

```cpp
return 0;
```

Last line, phew. I won't go into the detail right now since we'll look at return statements when dealing with functions. For now, you must know that we need to *return*
a value back to the program which called `main`. Typically, this is the OS itself. The value denotes whether your program exited successfully. Since nothing bad
really happened, we return 0. If you return anything other than 0, it means "something bad happened and it couldn't finish without errors".

*Don't* omit the return statement. Even when the compiler only warns you, it's good practice to inform the OS about the program's termination.

## Conclusion

There we go, this is the reason why you get `Hello World!` as output. Let's recap what you've learned:

- `#include` is a preprocessor directive that includes a file by copy-pasting it
- The main function is the entry point of your program
- `std::cout` can be used to print to the console
- `""` creates a string with given characters
- `std::endl` ends the console line and updates it immediately
- Returning 0 from `main` means "success", everything else "error"

## Exercises

Your first two exercises!
1) Try printing something else to the console by modifying the string
2) Try printing two strings on the same line

## Next up

Congratulations, you finished Act **Getting Started**! Time to explore the basics of C++ in the next Act, see you there!
