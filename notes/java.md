# JAVA

[⬅️ Back to home](/my-guide)

## Quiz

What is Java?
Why use Java?
What are low level languages and why are they called as such?
What are high level languages and why are they called as such?



## Notes

1️⃣🚩Reference
[Course: Java In-Depth: Become a Complete Java Engineer! by Dheeru Mundluru from Udemy](https://www.udemy.com/course/java-in-depth-become-a-complete-java-engineer/)

### Java - a High level overview

#### What is Java ?

A General purpose(not dependednt on any domain, can be used to develop wide variety of applications), object-oriented(helps real world scenarios), platform independent(write once and run anywhere), concurrent(multi-threading) programming language that runs very fast.

Assembly Language ----> assembler ----> Machine language
Source code(High level languages) ----> Compiler ----> target language

#### Compiler

**Compilation** -> Converting of sourcecode to target language(machine code, byte code, programming lanugage),

1. it verifies syntax and semantics
2. Code optimization
3. Generates machine code

source code ---> [compiler] ---> machine code ---> [CPU] ---> results

Pros                   | Cons
:----                  | :----
Fast execution         | No platform independence
No compilation step       | Interpreter is loaded into the memory
Easier to update |

#### Interpreter

**Interpretation** -> Directly executing source code to get results

1. Its a virtual machine that simulates a CPU
2. It executes pre-compiled machine code in its library for each command in the language, it doesn't generate machine code.

source code ---> [Interpreter] ---> results

Pros         | Cons
:----        | :----
Platform independence        | Slow, costly memory access, Source code is reinterpreted every time
No compilation step       | Interpreter is loaded into the memory
Easier to update |

> Java uses compilation for fast execution and interpretation for platform independence.

Java Source code --> [Java compiler] --> Java bytecode --> [Java interpreter] --> result

