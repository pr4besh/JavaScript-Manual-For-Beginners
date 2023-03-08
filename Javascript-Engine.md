# Javascript Engine

JavaScript engine is a software or a progrma responsible to run our JavaScript code. Almost every modern day browsers we use have their own JavaScript engine runnning in the background. Some of the most popular JavaScript engine are -

* __v8__ - Developed by __Google___ for __Chrome__
* __SpiderMonkey__ - Developed by ___Mozilla___ for __Firefox__
* __JavaScriptCore__ - Developed by ___Apple___ for Safari
* __Chakra__ - Developed by ___Microsoft___ for __Edge__

___Brendan Eich is the creator of JavaScript language and the co-founder of Mozilla project.___

## Inside the JavaScript Engine

Computers can only understand binary (0s and 1s) which is the reason our computer program needs to be converted into machine code. We convert our program into machine code via compilation or interpretation. 

#### Compilation

During compilation, the entire source code is converted into machine code all at once. The code is written into a portable file that can be executed anywhere- regardless of platform or operating system. The program is first converted into machine coe and later executed on the machine. The execution of the machine code happens right after the compilation. 

#### Interpretation

During interpretation, the interpreter runs through the source code and executes it line by line. The code is read and executed at the same time. The conversion of code into machine code does not happen of time, instead, right before execution. Interpreted programming language are much slower in terms of performance when compared to compiled language. 

## Just in Time (JIT) compilation in JavaScript

Although most people consider JavaScript as an interpreted langauge, that is no longer the case. Modern JavaScript use the concept of both compilation and interpretation at the same time knows as ___Just-In-Time (JIT) Compilation___.

In this approach, whole program gets compiled into machine language at once and then it is executed. Unlike the compiled language like C, where the compilation is done ahead of time (before actual execution of code), with JavaScript, the compilation is done during execution.

### JIT Structure 


