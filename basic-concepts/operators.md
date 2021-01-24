# Operators

After getting scared by UB we'll take our time to relax a bit by looking at some basic operators.

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

As expecte we get

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

