# JAVA

[⬅️ Back to home](/my-guide)

## Quiz

* What is Java?
* Why use Java?
* What are low level languages and why are they called as such?
* What are high level languages and why are they called as such?
* Can you please specify what are programming languages which are compiled to another programming languages?
* Why are we using public for only one class?

    <details>
    <summary>▶️ Solution</summary>
    It is how it has been designed and I am not sure if the reason is  documented. But here is a good reason on why it is done that way. Let's  assume we have two public classes Y & Z in a  file named Y.java.  Now, let's assume a different class X is using Z.  Now, when we compile  X, the compiler first tries to locate Z.class and if it cannot find it,  then it tries to locate Z.java so that it can compile it automatically.  But, since we only have Y.java, the class Z  cannot be located and hence  we get a compilation error. So, we do need  to place them in separate  files.
    </details>

<!-- tooltips -->
*[JVM]: Java Virtual Machine
*[JIT]: Just In Time
*[JDK]: Java Development Kit
*[SDK]: Software Development Kit
<!-- tooltips end -->

## Documentation / Specification

[Java API 13](https://docs.oracle.com/en/java/javase/13/docs/api/index.html)
[Java SE specifications](https://docs.oracle.com/javase/specs/)

## Notes

1️⃣🚩Reference
[Course: Java In-Depth: Become a Complete Java Engineer! by Dheeru Mundluru from Udemy](https://www.udemy.com/course/java-in-depth-become-a-complete-java-engineer/)

### Java - a High level overview

#### What is Java ?

A General purpose(not dependent on any domain, can be used to develop wide variety of applications), object-oriented(helps real world scenarios), platform independent(write once and run anywhere), concurrent(multi-threading) programming language that runs very fast.

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
2. An interpreter does not generate machine code like a compiler, but it maintains a library of pre-compiled machine code and executes the appropriate machine code corresponding to the statement in the source code

source code ---> [Interpreter] ---> results

Pros                         | Cons
:----                        | :----
Platform independence        | Slow, costly memory access, Source code is reinterpreted every time
No compilation step          | Interpreter is loaded into the memory
Easier to update             |

> Java uses compilation for fast execution and interpretation for platform independence.

Java Source code --> [Java compiler] --> Java bytecode --> [Java interpreter] --> result

##### JVM

* JVM is the Java interpreter we use,
* JVM is platform specific or dependent which helps in achieving platform independence.
* Java bytecode is platform independent

> Java is a interpreted language as we are using JVM to interpret the Java byte code

**Commands used for compilation and interpretation of JAVA**
Java source code, `Hello.java` --> compile using `javac Hello.java` --> output is `Hello.class` (java bytecode) --> JVM executes it in any platform using `java Hello`

###### Execution speed of JVM(performance)

* Java bytecode is compact, compiled, and optimized which is Designed for JVM, and JVM interpretation of Java bytecode is much faster.
* Just-in-time(JIT) compilation(*Dynamic compilation*) by JVM.
* all your Java programs run under a Virtual Machine, a machine that is hidden, physically not available, abstract. Hence JVM is called *Abstract Computing Machine*
* Manipulates memory at runtime
* **JIT** It is a JVM component that perform dynamic compilation by converting frequently executed bytecode called "hot spots" into machine code. The compiled machine code is cached and used in future to achieve faster performance.
  
###### Core Responsibilities of JVM

* Loading and Interpreting Java bytecode
* Security
* Automatic Memory management

###### JVM Instance

* When we run java program using JVM command `Java Hello`, an instance of JVM is loaded into the memory which executes Java bytecode `Hello.class`.
* Single JVM instance run only one Java program
* Can run more than once JVM instance at a single time to run multiple java programs

###### JVM Architecture

![image](../images/java/JVM_architecture.drawio.svg)

1. JVM instance loads in memory
2. Get memory allocated to it for its use
3. **Class Loader** loads the Hello.class
4. **Bytecode Verifier** its verifies bytecode to ensure the loaded class is not corrupted
5. If there are not issues reported by the 'Bytecode Verifier' it is executed by then **Execution Engine**
6. **Execution Engine** includes **JIT Compiler** and **Interpreter**
7. **Garbage Collector** is responsible for automatic memory management
8. **Security Manager** is responsible for security, like having additional checks to stop executing of bytecode which can access the filesystem, and having it execute in more restricted environment called the sandbox environment

#### Java Software family

- Java Standard Edition(Java SE) - Standalone applications for desktops and servers
- Java Enterprise Edition(Java EE) - Large-scale applications for server, Built on Java SE
- Java Micro Edition(Java ME) - Applications for resource constrained devices, Users subset of SE

**Java SE** - is a set of specifications which includes *Java Language Specification(JLS)*, *Java Virtual Machine specification(JVMS)*, *Java API Specification*

**Java SE implementations(JDK's)** - are Oracle JDK(official), Oracle OpenJDK,AdoptOpenJDK, Amazon Corretto, Red Hat's OpenJDK etc..,

**JDK or Java SDK** - has *Dev tools*(like java compiler), *JVM*, *Java API*

![image](../images/java/JDK.drawio.svg)

**JSR** - Java specification request, describes the features added to a release, each release will have a JSR.
**JCP** - Java community process, The process of developing JSR through different stages.

#### Installation

jdk download from - https://www.oracle.com/java/technologies/downloads/

Windows:
*set environment variable*
`JAVA_HOME` to `C:\Program Files\Java\jdk-18`
*add to path*
`PATH` - add new `C:\Program Files\Java\jdk-18\bin` or `%JAVA_HOME%\bin`

uninstall -> control panel -> uninstall a program -> select `java 18` -> click 'uninstall'

#### Setting classpath

- a path on file system for locating `Java classes`
- using classpath in interpreter finds the class file when we are executing `java Hello`.
- classpath is only required if we are compiling and running the programs from command line.

Windows:
*set environment variable*
`classpath` to `.;`

#### Classes

* Object are created from a class

|Class |
| --- |
|variable declarations|
|constructors|
|methods|
|nested classes|

'Hello world' program in Java

```java

public class Hello {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```
