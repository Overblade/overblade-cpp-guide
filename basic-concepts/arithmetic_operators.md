# Arithmetic Operators

After getting scared by UB we'll take our time to relax a bit by looking at some basic arithmetic operators.

## What are operators?

Operators (like the name already implies) *operate* on variables/data. They take values (operands) and calculate something based on those values.

## Binary arithmetic operators

Binary arithmetic operators take two operands, perform some arithmetic on them and return a result. The probably most famous ones are the *addition and subtraction operators*.
Let's take a look at some examples:

```cpp
int a = 3 + 4;
int b = 1 - 3;
```

As you can see, addition utilizes `+`, subtraction `-`. So the expected results would be

```
a is 7
b is -2
```

Easy, isn't it?

The next two ones are `*` and `/`. Guess what they do? Exactly. Multiplication and division.

```cpp
int a = 3 * 5;
int b = 8 / 2;
```

As expected we get

```
a is 15
b is 4
```

However, consider

```cpp
int a = 5 * 3.7;
float b = 5 / 2;
```

Are you expecting 18.5 and 2.5? Well, you're wrong then.

Let's closely look at the multiplication first: 5 and 3.7 are multiplied with each other which obviously results in 18.5. But note to what type we assign the result.
An integer! And since integers can't hold floating-point numbers a *conversion* happens. In this case, the decimal part is cut-off so that only the integer part remains.
Consequently, the result is 18. We call this type of automatic conversion *implicit cast*.

The second example presents a different problem: Division looks at the type of the divisor (i.e. 2). Since the type of 2 is `int`, *integer division* happens here.
That means, the division is carried out and again, the floating-point part gets discarded. 5 divided by 2 yields 2.5, so the .5 gets discarded and we're left with 2.

Now, 2 is assigned to a variable of type `float`. Again, a type conversion happens from `int` to `float`, so `b` gets the value of `2.0`.

What if we had the following?

```cpp
float b = 5 / 2.0;
```

2.0 is a floating-point constant, so the divisor has the type `float`, causing the division to operate on floats. That way we obtain the expected `2.5` for `b`.

To conclude, `/` carries out integer division if the divisor has an integer type and floating-point division if the divisor has a floating-point type.

There is one last operator belonging to this group and is closely related to `/` for integer division: The modulo operator `%`.
Modulo returns the remainder of an integer division:

```cpp
int a = 5 % 2;
```

Since 5 divided by 2 yields 2 with a remainder of 1, `a` will hold the value 1.

Note that modulo only works for integers and having a divisor of 0 when performing integer division / modulo causes undefined behaviour. You should never try to divide by 0 anyways.

## Unary arithmetic operators

There are two more arithmetic operators although these only operate on *one* value (therefore *unary*): `+` and `-`

```cpp
int a = +5;
int b = -5;
```

I don't think we need to discuss the output, it should be fairly obvious. While it makes sense to have unary `-` to negate values, unary `+` *seems* to have no real use case.

Actually, it does two things we won't discuss in detail right now:
- Integer promotion (smaller types convert to int)
- lvalue to rvalue conversion (conversion to "temporary")

No need to know any of these effects yet, I'll just leave it here for completeness' sake.

## Increment / decrement operators

Two additional operators exist that allow incrementing / decrementing an arithmetic type. *Incrementing* means adding 1 to a variable while *decrementing* means subtracting 1
from a variable.

Let's look at some examples:

```cpp
int a = 5;
a++;
a--;
```

As you can see, these operators are also unary and only operate on variables. Therefore, `5++` is illegal.
Also, note that these operators operate on `a` directly. 

There is another variant of increment / decrement operators:

```cpp
int a = 5;
++a;
--a;
```

Here, the `++`/`--` comes *before* the variable whereas in the first example they appear *after* the variable. That's why the first version is called **postfix increment/decrement**
(or **post-increment/post-decrement** for short) and the second version  **prefix increment/decrement** (or **pre-increment/pre-decrement** for short).

Essentially, the difference between the two is the order of evaluation. Prefix operates *first* then returns the new value while postfix *first* returns the old value and then carries out the operation. There is no difference if you only use it to increment or decrement as one operation, but things change if we also use the result of it:

```cpp
int a = 5;
int b = ++a;

int c = 5;
int d = c++;
```

For `b`, `a` is incremented *first* so it does now hold the value 6, then it gets assigned to `b`. Consequently, `b` receives the value `6`.

For `d`, `c` returns the old value *first*, then increments. Therefore, `d` receives the value `5`.

To remember the rule always look at which side the `++`/`--` is attached to. If it's on the left, it already looks like a prefix and from there you can deduce that
it first carries out `++`/`--` (pre = before), *then* returns the value of the variable. Likewise, it's the opposite for postfix (since post = after).

One last subtle difference you might stumble upon in case you're wondering:

```cpp
int a = 5;
++a = 2;
```

This is legal. You'll understand the exact reason later, but prefix has the peculiarity of returning a *reference* to the variable. Meaning `a` increments, then gets assigned to 2. If you'd use postfix here the compiler will refuse to compile it.

For your interest, these operators cannot be used for bools since C++17. It doesn't make much sense to "increment a bool" anyways.

Oh, and never combine use of these operators on a variable with utilizing the same variable in the same expression. This is UB.

```cpp
int a = 2;
int b = a++ + a;
```

Illegal. Don't.

## Assignment operators

This group is fairly straightforward. We have already seen that `=` is used to *assign* one constant/variable to another one. Since it's fairly intuitive to use there's not much to explain more about it.

However, there is more than one assignment operator. Consider the following scenario:

```cpp
int a = 2;
a = a + 3;
```

Here we want to increment `a` by 3. Of course we won't use pre-/post-increment three times here. Instead, we *re-assign* to `a` the previous value of `a` added to 3.
There is a shorter way to express your intent:

```cpp
int a = 2;
a += 3;
```

At first glance it might look a bit confusing, it's something you have to get used to. Basically, `+=` adds the value on the right to the value on the left.

You can even create more complex expressions with this:

```cpp
int a = 5;
int b = 3;
a += a * b + 4;
```

which is shorthand for

```cpp
a = a + a * b + 4;
```

Use this shorthand assignment operator whenever you can, it aids readability of your code.

Obviously `+=` is not the only one. Every binary arithmetic operator can be combined with an assignment:

```cpp
int a = 4;
a += 4;
a -= 3;
a *= 8;
a /= 2;
a %= 7;
```

Pretty useful, isn't it?

## Parentheses

Remember when you learnt the order of operations? Multiplications prevail additions? The same applies to C++.

To accomodate this, parentheses can be used just like in plain maths:

```cpp
int a = 6;
int b = (a + 2) * 5;
```

Parentheses not only exist to force calculation of a different expression first but also to enforce *general operator ordering*. You must know every operator is ranked
by the standard and the lower the number the higher the precedence.

It's not too important to know all precedences so if in doubt rather use one more pair of parentheses than trying to find a nasty bug later. "C++ operator precedence" yields
lots of results on the internet in case you're curious.

## Conclusion

Wow, this was quite a lot. Knowing all the operators is fundamental for writing code. So let's quickly summarize which operators we've seen:

- Binary arithmetics: `+`, `-`, `*`, `/`, `%`
- Unary arithmetics: `+`, `-`
- Pre-/Postfix inc-/decrement: `++`, `--`
- Assignments: `=`, `+=`, `-=`, `*=`, `/=`, `%=`
- Parentheses: `()`

There are a couple more which are a bit difficult to explain without knowing some other basics first.

## Exercises

I'll give you a bunch of exercises to reinforce your newly gained knowledge:

1. Write a program that receives an integer from the user, then add 1, multiply by 3 and subtract 2 from it. Finally, print the result. 
If you can, use the shorthand assignment operators.

2. Write a program which negates the user's integer and decrements it afterwards.

3. Try to write code that gives you the remainder of an arbitrary division without using modulo.

Really try to give your best to master these three exercises. They allow you to better understand each operator.

## Next up

Well, since we know the first big group of operators now, the *arithmetic operators*, we'll look at *logical operators* in the next guide in order to prepare for our first
*conditional constructs*...

