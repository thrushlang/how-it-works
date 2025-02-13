# ¿How it works?

### > ¿How does the current thrush compiler work to compile with **LLVM**?

### First things first.

### ¿What is llvm?

LLVM (Low-Level Virtual Machine) is a set of tools and libraries that facilitate the creation of compilers and other code manipulation-related tools. It provides a modular infrastructure for intermediate representation (IR), code optimization, machine code generation, and execution.

<p align="center">
  <img src= "https://github.com/thrushlang/how-it-works/blob/master/assets/what%20da%20heck%20is%20llvm%3F.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

### ¿How does the thrushc compiler compile to LLVM intermediate code?

First of all, the compiler is written in **[Rust](https://www.rust-lang.org/)**. So we have easy access to the **LLVM-C bindings**, which is an API that allows generating corresponding IR for the C programming language. The raw **LLVM-C bindings** in Rust are from the **[llvm-sys](https://gitlab.com/taricorp/llvm-sys.rs)** crate. We use a wrapper around it, much simpler to use, called **[inkwell](https://github.com/TheDan64/inkwell)**, which is a Rust crate, which is a wrapper around the raw LLVM-C wrapper. We use Inkwell to generate the intermediate LLVM code, to then pass it to Clang so that it compiles it into its respective binary.

<p align="center">
  <img src= "https://github.com/thrushlang/how-it-works/blob/master/assets/what%20da%20heck%20compile%20thrushc%3F.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p
  
And at the end of the day, this is how the compiler works, at least at the moment. However, it does not represent the entire operation of the compiler, since there are optimization and verification phases of the intermediate code, but that is for another occasion.
