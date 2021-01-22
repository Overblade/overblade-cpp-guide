# Code

The question of all questions: What is code actually?

Simply said, code is text you write in order to *instruct* the computer to do certain things. This includes not only desktop programs but also embedded devices
such as microcontrollers present in most electrical devices.
However, the code must be *translated* into a language the device actually understands.

This process is known as *compilation*. A **compiler** is a program that performs exactly this task for you.

## But why do we actually need a compiler?

Well, you must know the compiler translates your code into something that is referred to *machine code*. Machine code is literally raw bytes, 0's and 1's.
The *processor* is the device executing this sequence of bytes and performs operations based on their value.

The reason why we don't write raw bytes is simple: Something like printing to a console or displaying something on screen takes an *insane amount of operations*.
We're not talking about tens or hundreds of operations but rather ten thousands to millions. Something we definitely don't want to spend time on.

This includes operations your application cannot perform by itself. Certain operations are implemented in the so-called **Operating System** or **OS** for short
which manages all kinds of user/device interactions. Common examples for operating systems include *Windows*, *Android* or *MacOS*.

So, the idea of writing code is to *abstract away* system-dependent operations and to reduce development time.

## The build process

The process of compiling your code into a binary is called *building*. Understanding the building process is fundamental: I've seen lots of beginners struggling with
weird build errors without knowing what was actually going on. Let's walk through it step-wise.

**1) Writing code**

Obviously we have to write some code first. We write the code into *source files* (.cpp) and *header files* (.h/.hpp). We'll learn later more precise definitions
of the two, but for now you just need to know most of the code is written in source files.

Like I already said, you don't need to write everything yourself. You can include *libraries* which expose certain functionality to your source file.
C++ comes with a *standard library*, known as the *C++ Standard Library*. The library is so big that it takes years to master most of it. If you need something,
it's most likely in the standard library. Internally, the standard library contains platform-dependent code which allows to interface OS functionality
without dealing with the OS yourself.

**2) Preprocessor**

Now, when you build your program the first step is running it through the **C-Preprocessor**. It is called like that because C and C++ share the same preprocessor.
The preprocessor's job is to scan through your files and performs certain tasks on them. This is controlled by preprocessor directives which you'll soon learn.

At this step, your code *hasn't* been translated yet.

**3) Compilation**

Step 3 is where the actual compilation happens. The compiler is supplied with all *compilation units*. A *compilation unit* is essentially a source file ran through
the preprocessor. As a result, the compiler has no such concept of a header file. It only sees compilation units.

At compilation, the compiler parses your code and checks whether your syntax is correct. After that, it translates your code into *object code*.
The distinction is necessary since we don't have runnable code *yet*.

**4) Linking**

This is perhaps the most confusing step for beginners because the linker does a lot of things at once and is rarely well explained.
Remember that the compiler translates individual compilation units? If we further think about it, we got **object files** *per compilation unit*.
So we somehow need to merge these files into one executable, which is exactly what the linker does. It *links* those files into one, references external code
supplied by libraries (such as .dll's on Windows) and adds some special code to make your program runnable by the OS.

And this is it! The program is runnable now if you wrote valid code or it might have failed with some kind of error, so the process might stop prematurely.

In the next guide I'll show you how to set up your environment to be able to finally write our first code. Doesn't it sound exciting?
