# Undefined behaviour

You might be surprised by the title but this is one of those topics being rarely taught in other tutorials. *Undefined behaviour* is a core concept of C++ even
though not really a good one. Knowing it is vital to write stable and robust code.

## The exercise of doom

Let's consider exercise 2 of the variables guide. I told you to

> Omit capturing input at all (i.e. remove the line with std::cin). What happens now?

Wanna know something? I told you to do something you *shouldn't have done*. Why, you ask? 

Well, I don't know what happened. If you think you know what happened, you're wrong. I asked you to jump into a hole and you might have blindly followed my order.
And this is exactly what this guide is about and why I explain this concept that early. 

*Never blindly copy code or use it in an unintended way.* ***Never.***

## Why the example is dangerous

Let's dissect the code.

```cpp
#include <iostream>

int main(){

	int number;
	std::cout << number << std::endl;

	return 0;

}
```

First, we defined a variable named `number` as an integer. Next up, we print it to the console.

Hol' up!

> We print it to the console.

*What* are we printing to the console? *We never assigned a value to the variable!*

And this is exactly the point: You entered the territory of **Undefined Behaviour**.

## Definition

**Undefined behaviour** happens when you meet a certain condition/case which the standard doesn't cover explicitly.
With other words, if you do something not covered by the standard, anything could happen:

- It could work
- It could crash
- It could show you a nice bluescreen
- It could cook coffee
- It could destroy the earth

In most cases it will appear as a *bug* in your program, though. A bug is some kind of error that is not immediately apparent but causes weird behaviour at runtime.

You might be wondering: *Why doesn't undefined behaviour even exist? Were they too lazy to fill holes in the standard?*

No, they weren't. You will progressively notice that C++ is focused on performance in contrast to other languages. Adding safety checks everywhere would slow down your
program quite a lot, so instead of doing this the standard decided it should be up to the coder to handle such special cases properly.

Undefined behaviour is everywhere, especially in the places you least expect it. But don't worry, if there's a case where one might commonly enter undefined behaviour
I will inform you about it.

## A word about initialization

*Initialization*, or "the act of setting a variable's value before use" is crucial in C++. Unlike other languages, C++ does *not* initialize variables to 0.
It picks whatever was in the memory before and as you might notice this could be anything. 

**If you leave a variable uninitialized, its contents are undefined.**

Don't do this:

```cpp
float a;
std::cout << a << std::endl;
```

Instead, do this:

```cpp
float a = 3.45;
std::cout << a << std::endl;
```

In the first example we cannot predict the value of a while in the second example we can, namely 3.45.
Note that not in every case not-initializing a variable causes undefined behaviour. We'll learn those exceptions later.

So, if you ever see a variable uninitialized consider initializing it explicitly.

Let's look again at the example from the variables guide:

```cpp
#include <iostream>

int main(){

	int number;
	
	std::cin >> number;
	std::cout << number << std::endl;

	return 0;

}
```

You might be wondering why we didn't initialize here. Well, cin overwrites `number`'s contents anyways so even if we initialized it it wouldn't be necessary.

As long as we don't *read* before we *write for the first time* we're good. Nontheless it's good practice to initialize every variable to a known value before use.

## Spotting undefined behaviour

I'm sorry to tell you there is no way to spot it without knowing a certain case inhibits undefined behaviour. Your best bets are always

1) Knowing when undefined behaviour happens (and therefore avoiding it)
2) Listening to the compiler's warnings

Today's compiler can spot lots of cases which would be undefined behaviour but don't rely on it finding all of them. Some language constructs are *extremely*
dangerous to use and have several rules about when undefined behaviour happens and when not. Beware of those.

## Conclusion

From now on we'll abbreviate undefined behaviour as UB. What did we learn today?

- UB happens when you meet a condition which is not covered by the standard
- UB is dangerous and unpredictable
- It's there to guarantee C++'s performance
- Always write (or better: initialize) a variable before reading from it

## Exercises

None, since I won't give you a task to practice UB :P

## Next up

In the next guide you will learn some basic arithmetic operations.
