# Setting up

So, to write and build code we need 4 things:

- Text editor
- Preprocessor
- Compiler
- Linker

Most of the time the latter three are bundled together in what we call a *toolchain*. Toolchains are collections of tools used to create your final program.
Meaning we only need two things: A decent text editor and a toolchain.

You could write your code in any text editor, really. However, coders usually use an IDE. IDE stands for *Integrated Development Environment* and is a program
which allows you to write your code in an editor and at the same time does all the building for you in the background.
What makes them even more useful is the fact it highlights syntax, offers auto-completion capabilities and can even show potential errors.

I really recommend to use an IDE as a beginner and only get separate tools if you know what you do. There are various IDE's around for different operating systems.

Now that you got your IDE installed, start a new project with any name and it should present you a folder structure for your project.
Create a new file named main.cpp if it hasn't for you already. Paste the following code example:

```cpp
#include <iostream>

int main(){

    std::cout << "Hello World!" << std::endl;
    return 0;
    
}
```

Now, click the build & run button (which typically looks like a green arrow) and you should get the following output:

```
Hello World!
```

Awesome! Your first C++ program! In case it failed, make sure you set everything up properly. The internet is pretty useful for fixing IDE errors.

The next step will be dissecting this piece of code which is also known as the *Hello World Program*. It's used to demonstrate a basic example of how code looks like.
