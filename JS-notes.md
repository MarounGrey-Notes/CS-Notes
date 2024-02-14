# Terminology

**Paradigms:** Approaches and mindsets of structuring code, which will direct your coding style and technique. <br>
**Concurrency model:** how Javascript engine handles multiple tasks happening at the same time. <br>
**Thread (in computing):** set of instructions that is executed on the computer's cpu. <br>

# How JavaScript works behind the scenes

* **High Level:** Javascript doesnt require to use resources (like memory).
* **Garbage-collected:** Cleaning memory so we dont have to.
* **Interprited or just-in-time compiled:** Conversion to machine code happens inside the JavaScript engine.
*  **Multi-paradigm:** Javascript uses multiple Paradigms:
    1. Procedural Programming
    2. Object-oriented programming (OOP)
    3. Functional programming (FR)
* Prototype-based object-oriented
* **First-class functions:** In a language with **first-class functions**, functions are simply **treated as variables**. We can pass them into other functions, and return them from functions.
*  **Dynamically-typed language:** No data type definitions. Types become known at runtime and can be changed automatically.
*  **Single-threaded:** JavaScript runs in one **single thread**, so it can only do one thing at the time.
*  **Non-blocking event loop:** Tasks that are taking too long to execute are getting executed in the "background" and get back in the main thread once they are finished.

# JavaScript Engine and Runtime
JS Engine - program that executes javascript code <br>

                                                      Runtime in the Browser
            *************** JS Engine ***************                     *************** Web APIs *************** 

                +++++++++++++++     +++++++++++++++                           ++++++++++++++++++++++++++++++   Functionalities provided 
                +             +     +   #    #    +                           +     DOM     +    Timers    +   to the engine, accessible
                +             +     +           # +                           ++++++++++++++++++++++++++++++   on window object.
                +             +     +     #       +                           +  Fetch API  +    . . .    + 
                +             +     +   #      #  +                           ++++++++++++++++++++++++++++++
    Execution   + ########### +     + #    #      +     Object in           
    context ->  + ########### +     +   #   #     +  <- memory             *************** Callback Queue *************** 
                +++++++++++++++     +++++++++++++++                         
                   CALL STACK             HEAP                               Click      Timer     Data     . . .
                                                                             
                Where our code      Where objects                          Example: callback function from DOM event listener
                is executed         are stored
                
                
                Event Loop takes callback function from the callback queue and puts them in the callstack so that they can be executed.
                Event Loop is essential for non-blocking concurrency model
                
                Runtime in Node.js: instead of Web APIs it uses C++ bindings and thread pool.
       
       
# Compilation vs Interpretation

**Compilation:** Entire code is conveted into machine code at once, and written to a binary file that can be executed by a computer. <br>
                           
        +++++++++++++++++        Step 1          ++++++++++++++++++++++++++++++++         Step 2         +++++++++++++++++++++
        +  Source Code  +     ------------->     +  Portable file: machine code +     ------------->     +  Program running  +
        +++++++++++++++++      Compilation       ++++++++++++++++++++++++++++++++        Execution       +++++++++++++++++++++
        
        Execution can happen way after compilation
                                                  
**Interpritation:** Interpreter runs through the source code and executs line by line.

        +++++++++++++++++            Execution Line by Line            +++++++++++++++++++++
        +  Source Code  +     ------------------------------------>    +  Program running  +
        +++++++++++++++++                                              +++++++++++++++++++++
        
        Code still needs to be converted to machine code (it happens right before its executed and not ahead of time)
        
Interprited languages are much slower then compiled. Modern JavaScript uses mix between compilation and interpritation which is called **Just-in-time (JIT) compilation:** Entire code is converted in machine code at once, then executed immediately.

        +++++++++++++++++        Step 1          ++++++++++++++++++++++++++++++++++++++++                    Step 2                    +++++++++++++++++++++
        +  Source Code  +     ------------->     +  Machine code (NOT a portable file  +     ------------------------------------>     +  Program running  +
        +++++++++++++++++      Compilation       +++++++++++++++++++++++++++++++++++++++        Execution (Happens immediately)        +++++++++++++++++++++
        

# Execution Contexts and The Call Stack

**Execution Context:** Environment in which a piece of JavaScript is executed. Stores all the necessary information for some code to be executed. <br>
Compilation -> Creation of global execution context(for top-level code) -> Execution of top-level code (inside global EC) -> execution of functions and waiting for callbacks <br>
**Call Stack** is a "place" where execution contexts get stacked on top of each other, to keep track of where we are in the execution.
### What's inside execution context?
Generated during "creation phase", right before execution.<br>
1. Variable Environment
    * *let*, *const* and *var* declarations
    * Functions
    * arguments object
2. Scope chain
3. *this* keyword
Note: Arrow functions do not have their *arguments objects* nor *this* keyword. Instead, they can use the arguments objects and this keyword from their closest regular function parent.

# Scoping and Scope in JavaScript: Concepts
* **Scoping:** How our program's variables are organized and accessed. "Where do variables live?" or "Where can we access a certain variable, and where not?"
* **Lexical scoping:** Scoping is controlled by placement of functions and blocks in the code.
* **Scope:** Space or environment in which a certain variable is declared (variable environment in case of functions). There is global scope, function scope, and block scope. Only *let* and *const* variables are block-scoped. Variables declared with *var* end up in the closest function scope.
* **Scope of a variable:** Region of our code where a certain variable can be accessed.

![alt text](https://github.com/MarounGrey-Repos/Pics/blob/main/2022-05-10.png?raw=true)
![alt text](https://github.com/MarounGrey-Repos/Pics/blob/main/Screenshot%202022-05-10%20220906.png?raw=true)


-------

# Different ways to write loops in JavaScript
Here are some common ways to iterate loops in JavaScript along with code examples:

**for loop**

```js
for(let i = 0; i < arr.length; i++) {
  // Prints each array element  
  console.log(arr[i]);
}
```

**while loop**

```js 
let i = 0;
while(i < arr.length) {
  console.log(arr[i]);
  i++;
}
```

**forEach**

```js
arr.forEach(function(element) {
  console.log(element);
});
```

**for...of loop** 

```js
for(let element of arr) {
  console.log(element); 
}
```

**for...in loop**

```js
for(let index in arr) {
  console.log(arr[index]);
} 
```

**map**

```js
arr.map(element => {
  console.log(element);
});
```

So in summary, for loops, while loops, forEach, for..of, for..in, and maps allow iterating in different ways useful in different situations.

Here are arrow function versions for some of the loop constructs in JavaScript:

**forEach**

```js 
arr.forEach(element => {
  console.log(element); 
});
```

**map**

```js
arr.map(element => {
  return element * 2;  
});
```

**forEach with index**

```js
arr.forEach((element, index) => {
  console.log(index, element);
});
```

**filter**

```js
const filtered = arr.filter(num => {
  return num > 5; 
});
``` 

**find**

```js 
const found = arr.find(el => {
  return el.id === 100;
});
```

**reduce** 

```js
const sum = arr.reduce((accumulator, current) => {
  return accumulator + current;
}, 0);
```

Arrow functions provide a concise way to supply anonymous callback functions, especially for array functional methods like map, filter, reduce etc.

------

## Example of the coding problem
Given 2 arrays check if they contain the same letter, if they do return true, othervise return false.
* are inputs always arrays?
* how large are the arrays gonna get?
### Solve a problem with O(n^2) [O(arr1*arr2)]
```
arr1 = ['a', 'b', 'c', 'x'];
arr2 = ['z', 'y', 'a'];

for (let i = 0; i < arr1.length; i++) {
    for (let j = 0; j < arr2.length; j++) {
        if (arr1[i] === arr2[i]) {
            return true;
        }
    }
}
return false
```
#### Solve a problem with better performance, O(n) [O(arr1+arr2)]
```
arr1 = ['a', 'b', 'c', 'x'];
arr2 = ['z', 'y', 'a'];

let map = {};
for (let i = 0; i < arr1.length; i++) {
    if(!map[arr1[i]]) {
        const item = arr1[i];
        map[item] = true;
    }
}
for (let j=0; j < arr2.length; j++) {
    if (map[arr2[i]]) {
        return true;
    }
}
return false;
```
