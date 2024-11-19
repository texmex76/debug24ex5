# Debugging 24/25 Exercise 5

There are two parts to this exercise:

1. Use static code analysis and fill out `CODE_ANALYSIS_REPORT.md`

- **Do not forget the report!**

2. Add support for multiplication in the bignum library and in the LISP parser

You can discard the separate bignum executable if you like. From now on, we will only work with the LISP parser.

# Checklist

- [ ] Use a static code analysis tool
- [ ] Fill out `CODE_ANALYSIS_REPORT.md`
- [ ] You MUST NOT use `+`, `-`, `*`, `/` for bignum operations
- [ ] Add signed multiplication support to the bignum library
- [ ] Adjust the LISP parser to support multiplication
- [ ] Check your programs and the report word count using the tools in `test/`
- [ ] **Provide detailed build and run instructions for linux CLI**

For more details, read the exercise sheet!

# Bignum Multiplication Tutorial

Following is one way of multiplying two **unsigned** bignums. Your LISP parser must support **signed** multiplication, so you must take the absolute value of the two bignums first and keep track of each sign. You are, however, also welcome to implement [two's complement multiplication](https://stackoverflow.com/questions/20793701/how-to-do-two-complement-multiplication-and-division-of-integers).

- Function `bignum_multiply(a: bignum, b: bignum, result: bignum)`
- Initialization:
  - Create a temporary bignum to store intermediate results.
  - Create a temporary bignum to store shifted values of `a`.
  - Set the result bignum to zero.
- Iterate through bits of `b`:
  - For each bit in `b`, starting from the least significant bit:
    - If the current bit of `b` is 1:
      - Shift `a` to the left by the position of the current bit.
      - Check if an overflow occurred during the shift. If so, signal an error and exit.
      - Add the shifted `a` to the result.
      - Check if an overflow occurred during the addition. If so, signal an error and exit.
- The final value in the result bignum is the product of `a` and `b`.
