## What Is Performance Analysis?

Ever found yourself debating with a coworker about the performance of a certain piece of code? Then you probably know how hard it is to predict which code is going to work the best. With so many moving parts inside modern processors, even a small tweak to the code can trigger significant performance change. That’s why the first advice in this book is: *Always Measure*. Many people rely on intuition when they try to optimize their application. And usually, it ends up with random fixes here and there without making any real impact on the performance of the application.

Inexperienced developers often make changes in the source code and hope it will make it faster. One such example is replacing `i++` (pre-increment) with `++i` (post-increment) all over the code base, assuming that the previous value of `i` is not used. In the general case, this change will make no difference to the generated code because every decent optimizing compiler will recognize that the previous value of `i` is not used and will eliminate redundant copies anyway. 

Many micro-optimization tricks that circulate around the world were valid in the past, but current compilers have already learned them. Additionally, some people tend to overuse legacy bit-twiddling tricks. One of such examples is using [XOR-based swap idiom](https://en.wikipedia.org/wiki/XOR_swap_algorithm),[^2] while in reality, simple `std::swap` produces faster code. Such accidental changes likely won’t improve the performance of the application. Finding the right place to fix should be a result of careful performance analysis, not intuition or guessing.

There are many performance analysis methodologies that may or may not lead you to a discovery. Approaches presented in this book have one thing in common: they are based on collecting certain information about how a program executes. Any change that ends up being made in the source code of a program is driven by analyzing and interpreting collected data.

[^2]: XOR-based swap idiom - [https://en.wikipedia.org/wiki/XOR_swap_algorithm](https://en.wikipedia.org/wiki/XOR_swap_algorithm)