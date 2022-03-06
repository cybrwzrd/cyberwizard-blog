+++
ShowReadingTime = true
date = 2022-03-06T06:11:33Z
disableShare = false
title = "The Wonderful World of Binary, Hex, and Decimal"
[cover]
alt = "Binary digits"
caption = "Don't you just love binary?"
hidden = false
image = "/uploads/bin2.jpg"
relative = true

+++
In this post we'll learn about binary, hex, and decimal numbering systems. We'll learn what a 'base' is, as well as how to convert between different bases. We'll also look at why these different number systems are so useful, and some of their most common use cases.

## What's in a base?

> In a positional numeral system, the radix or base is **the number of unique digits, including the digit zero, used to represent numbers**.

Um, thanks Wikipedia. Not the most enlightening is it? Simply put, a "base" is the _base set_ of **digits** that you can use to represent numbers. So, binary is base 2. The only two digits used to represent numbers in binary are 1s and 0s. Easy right? Once you exhaust the base set of digits, you increment the next column and continue.  That is _7, 8, 9, 10._

### Decimal (base 10)

Decimal, or base 10, is what you're probably used to dealing with on a daily basis. There are 10 digits used to represent decimal numbers:

> 0, 1, 2, 3, 4, 5, 6, 7, 8, 9

![Decimal](/uploads/decimal.png)

The handy thing about decimal is that working in groups of 10 makes for nice easy math, as we'll see shortly.

### Binary (base 2)

Binary, or base 2 is the simple yet beautiful numbering system of computers. Everything from numbers, text, and even images can be represented with these two numbers.

![Binary](/uploads/binary.png)

> As the saying goes - _there's 10 types of people in the world; those who understand binary, and those who don't._

### Hexadecimal (base 16)

While it may sound quite intimidating, hexadecimal (or base 16), is actually more commonplace than you may realise.  While often used to condense binary numbers into a more concise representation, hexadecimal (or hex for short) is used for color codes in web design - hence _hex_ codes.

For example, #FFFFFF, which is the hex code for the color white, is actually comprised of 3 groups of hexadecimal numbers: `FF`, `FF`, and `FF`. These 3 groups represent the color values for the red, green, and blue color channels. As we'll see shortly, `FF` in hex equates to `255` in decimal.  We can see then that hex codes can be viewed as a more concise way of representing `rgb(255, 255, 255)`. Isn't that neat!

You may have already realised "hey wait, we use 16 digits for base 16, but there's only 10 numeric digits in the latin alphabet!". Because we need an additional 6 digits, we use the letters `A`, `B`, `C`, `D`, `E`, and `F` to fill the gap.  This is entirely arbitrary however, we could have chosen any 6 letters, or names of fruit, or Simpsons characters, had we chosen to.

![Hexadecimal](/uploads/hex.png)

## The number Ten doesn't exist!

Wait, what? Yeah that's right. The number "ten" doesn't actually exist.  "Ten" (as well as eleven, twelve etc) is really just a convenient way to describe the number `one zero`.  As soon as you grasp this, understanding how different bases represent numbers becomes much easier.

If you're still confused, fear not reader! We'll go over this more in the next few sections.

## Understanding how each base represents numbers

First let's have a look at some representations of numbers in each base, starting with zero through twenty, and throwing an assortment of larger numbers in for good measure.

### Comparison of each base

| Binary | Decimal | Base 16 |
| --- | --- | --- |
| 0 | 0 | 0 |
| 1 | 1 | 1 |
| 10 | 2 | 2 |
| 11 | 3 | 3 |
| 100 | 4 | 4 |
| 101 | 5 | 5 |
| 110 | 6 | 6 |
| 111 | 7 | 7 |
| 1000 | 8 | 8 |
| 1001 | 9 | 9 |
| 1010 | 10 | A |
| 1011 | 11 | B |
| 1100 | 12 | C |
| 1101 | 13 | D |
| 1110 | 14 | E |
| 1111 | 15 | F |
| 10000 | 16 | 10 |
| 10001 | 17 | 11 |
| 10010 | 18 | 12 |
| 10011 | 19 | 13 |
| 10100 | 20 | 14 |
| 10101 | 21 | 15 |
| 11111 | 31 | 1F |
| 1000101 | 69 | 45 |
| 11111111 | 255 | FF |

As you can see in the table, binary numbers start getting quite large and unwieldy quite quickly, hence why hex is used commonly as a more concise representation. In fact

### What base am I looking at?

## Converting between bases

## Wrap Up