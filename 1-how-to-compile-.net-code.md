# Implicit Compilation
 Implicit compilation is a two-step process.  The first step is converting the source code to intermediate language (IL) by a language-specific compiler. The second step is converting the IL to machine instructions. The main difference with the explicit compilers is that only executed fragments of IL code are compiled into machine instructions, at runtime. The .NET framework calls this compiler the JIT (Just-In-Time) compiler.

The implicit way delivers portability quite more effortlessly, because the first step of the process is much more platform agnostic. Each target platform has a JIT compiler deployed and as long as the IL can be interpreted the program can execute. The initial compiler does not need to know all of the places where the software might run.

# Just-In-Time Compilation    
The JIT compiler is part of the Common Language Runtime (CLR). The CLR manages the execution of all .NET applications. In addition to JIT compilation at runtime, the CLR is also responsible for garbage collection, type safety and for exception handling.

![x](https://www.telerik.com/sfimages/default-source/blogs/understanding--net-just-in-time-compiler-figure-170ea752614cf-png)

Different machine configurations use different machine level instructions. As Figure 1 shows, the source code is compiled to exe or dll by the .NET compiler. Common Intermediate Language (CIL) consists of instructions that any environment supporting .NET can execute and includes metadata describing structures of both data and code. The JIT Compiler processes the CIL instructions into machine code specific for an environment. Program portability is ensured by utilizing CIL instructions in the source code. The JIT compiler compiles only those methods called at runtime. It also keeps track of any variable or parameter passed through methods and enforces type-safety in the runtime environment of the .NET Framework.

## **Please review**

![](https://codeasy.net/ContentStorage/Chapters/f3fc0263-1d53-464f-8b3a-340cc1d772db/Assets/c_sharp_program_execution.png)

![](https://codeasy.net/ContentStorage/Chapters/f3fc0263-1d53-464f-8b3a-340cc1d772db/Assets/net_structure_2.png)
