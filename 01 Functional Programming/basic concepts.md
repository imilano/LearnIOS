# 函数式编程简介

Wikipedia 这么介绍 Swift：
> Swift is a general-purpose, multi-paradigm, compiled programming language developed by Apple Inc. and the open-source community, first released in 2014. Swift was developed as a replacement for Apple's earlier programming language Objective-C, as Objective-C had been largely unchanged since the early 1980s and lacked modern language features. Swift works with Apple's Cocoa and Cocoa Touch frameworks, and a key aspect of Swift's design was the ability to interoperate with the huge body of existing Objective-C code developed for Apple products over the previous decades. It is built with the open source LLVM compiler framework and has been included in Xcode since version 6, released in 2014. On Apple platforms, it uses the Objective-C runtime library which allows C, Objective-C, C++ and Swift code to run within one program.

从中可以看到，Swift 是多范式的，现代化的，面向未来的下一代苹果官方开发语言。 Swift 的创造者 Chris Lattner 把 Swift 简单描述为”没有 C 的 Obeject C“。Swift 中引入了函数式编程的概念，极大扩张了语言设计的空间。故而在此对函数式编程的基本概念做个简单总结。

从Wikipedia 上我们可以扒出这么一段对 Functional Programming 的介绍：
> In computer science, functional programming is a programming paradigm where programs are constructed by applying and composing functions. It is a declarative programming paradigm in which function definitions are trees of expressions that map values to other values, rather than a sequence of imperative statements which update the running state of the program.
> 
> In functional programming, functions are treated as first-class citizens, meaning that they can be bound to names (including local identifiers), passed as arguments, and returned from other functions, just as any other data type can. This allows programs to be written in a declarative and composable style, where small functions are combined in a modular manner.
>
> Functional programming is sometimes treated as synonymous with purely functional programming, a subset of functional programming which treats all functions as deterministic mathematical functions, or pure functions. When a pure function is called with some given arguments, it will always return the same result, and cannot be affected by any mutable state or other side effects. This is in contrast with impure procedures, common in imperative programming, which can have side effects (such as modifying the program's state or taking input from a user). Proponents of purely functional programming claim that by restricting side effects, programs can have fewer bugs, be easier to debug and test, and be more suited to formal verification.

从中可以总结出这么几点：
- 函数式编程是声明式编程的一种。
- 函数式编程中最重要的概念是函数。
- 函数是一等公民，不仅可以作为参数，还可以绑定到变量上，甚至可以作为函数的返回值。
- 函数式编程也是纯函数式编程的同义词，后者是函数式编程中的一个子集。
- 纯函数（pure function）意味着 deterministic。也就是说，对于同样的输入参数，函数产生的结果总是相同的，不会被 mutable state 影响，也不会产生side effect。


下面是是函数式编程语言的几个概念。
- First-class and higher-order functions
  First-class function 指的是编程语言能够把函数视为第一等公民；Higher-order function 指的是函数能够接受函数作为参数，也能够把函数作为返回值。二者有相似，但是属于不同领域的不同概念。
- Pure functions
  纯函数意味着没有副作用，而这为程序优化带来了几个好处：
  - 如果函数产生的结果没有被用到，那么这个结果可以安全地删除，且不会对其他语句产生影响。
  - 如果调用不会造成副作用的带参函数，那么对于同样的输入参数，程序调用的结果是幂等的。
  - 对于没有数据依赖的两个表达式，他们的顺序可以颠倒，甚至可以并行执行。
  - 如果语言本身不允许 side effect，那么就可以采用任何的求值策略。这在编译器优化的时候很有帮助。 
- Recursion
- Strict versus non-strict evaluation
  
  函数式编程可以根据其为strict evaluation 还是 non-strict evaluation 而分为两类，这主要跟表达式求值时，函数参数如何处理相关：
  > In brief, strict evaluation always fully evaluates function arguments before invoking the function. Lazy evaluation does not evaluate function arguments unless their values are required to evaluate the function call itself.

  简单来说，strict evaluation 意味着在调用函数之前，参数必须被 fully evaluated，也就是说参数必须是确定的值；而 lazy evaluation 则不然。
- Type system
- Referential transparency
  
  > Functional programs do not have assignment statements, that is, the value of a variable in a functional program never changes once defined. This eliminates any chances of side effects because any variable can be replaced with its actual value at any point of execution. So, functional programs are referentially transparent.

  函数式程序没有赋值语句，意味着变量一旦定义，值就不会再改变，从而具有很好的引用透明性。引用透明性意味着表达式的值能够随意替换而不影响程序的行为。
- Data structures
  
  函数式编程的数据结构与命令式编程的数据结构稍有不同。