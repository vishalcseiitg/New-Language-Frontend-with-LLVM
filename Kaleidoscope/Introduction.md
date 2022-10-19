This tutorial is illustrated with a toy language called “Kaleidoscope” (derived from “meaning beautiful, form, and view”). Kaleidoscope is a procedural language that allows you to define functions, use conditionals, math, etc. Over the course of the tutorial, we’ll extend Kaleidoscope to support the if/then/else construct, a for loop, user defined operators, JIT compilation with a simple command line interface, debug info, etc.

We want to keep things simple, so the only datatype in Kaleidoscope is a 64-bit floating point type (also known as ‘double’ in C parlance). As such, all values are implicitly double precision and the language doesn’t require type declarations. This gives the language a very nice and simple syntax. For example, the following simple example computes Fibonacci numbers:

# Compute the x'th fibonacci number.

```

def fib(x)
  if x < 3 then
    1
  else
    fib(x-1)+fib(x-2)

# This expression will compute the 40th number.
fib(40)

```

We also allow Kaleidoscope to call into standard library functions - the LLVM JIT makes this really easy. This means that you can use the ‘extern’ keyword to define a function before you use it (this is also useful for mutually recursive functions). For example:

```

extern sin(arg);
extern cos(arg);
extern atan2(arg1 arg2);

atan2(sin(.4), cos(42))

```

