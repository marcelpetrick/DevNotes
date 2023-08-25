# 20230825 Doulos: Python - Everything is an object

```
Introduction Python has become an incredibly popular language in the last few years doing everything from automating design flows, data analysis and even just being a general “glue” which can translate one dataset into another. For most everyday tasks, it “just works” but there are times when you can be caught out when something unexpected happens, especially if you are used to other types of programming languages such as C, C++, C# or Java. In this webinar... ​Dr Des Howlett and Loic Domaigne of the Doulos Senior Technical Staff, will show you how all parts of Python have a lot in common, whether they are variables, classes, class objects or functions. We will see what happens when a variable is assigned, when functions are called and when generators yield new values. This will help you to adjust any mental map that you acquired from other languages and make you better at Python. The webinar will be part theory and part practical demonstration. At the end, you will be able to download a Jupyter Notebook which you can run yourself and continue your investigations into the inner workings of this very powerful language. Are you ready to take the leap to Python? The webinar is presented in partnership with Toradex and concludes with a brief overview of the Toradex board portfolio and Torizon software platform. 
```

![](img00.png)
## short intro
* it just works in a normal way, used even by non-programmers
* there are times when it does things we might not be expecting
* they aren't wrong, just different
![](img01.png)

## topics
* conventional model
* storing regular variables
* definitions of functions and classes
* function calls and stack frames
* generators and multithreading
* higher order functions: functions which create and define other functions

## note
* some things like integers and Booleans are not handled quite like objects for efficiency reasons

## conventional view
![](img02.png)

## Python is different
![](img03.png)
* end goal is the same, but the way is different
* the type information goes with the value; not the variable name
* so y = X where x = 42, then we just create a new binding to that object
* sometimes more efficient, in case of 100 variables with the same value, then you just have 100 labels instead of 100 containers
* but 42 is now immutable
![](img04.png)
* integers are immutable, strings are immutable
* adding numbers just frees the initial object and since it is not bound to anything anymore, it is left for the garbage collector
* every object has 2 parts, the type and the data
```
x = 42
y = x
x += 10
print(f"x: {x}, y: {y}")
# x: 52, y: 42
```
* type of objects can change when the code continues
* x is free to be whatever you want it to be
* when an object is not bound anymore, and the garbage collector comes and says "nobody wants you, nobody knows you", then it is free to destroy it (deallocate/destroyed)
![](img05.png)
* multiplying strings? just repeat it, not multiplying the characters
* for most people this does not matter, because their programs are shortlived; and it also does not matter how data is stored
![](img05.png)
* identifier names in Python are more like a hybrid pointer/reference with RTTI in C++
* what about definitions (functions)?
![](img06.png)
* just a container 
* "class" just means to create an object bound to a name
  * the data part is the definition of the members of the class
  * giving the class a name will prevent the garbage collector to throw away the name
  * variables are just local to the function
  * there is no classical stack, just stack frame objects (for recursive functions): which is released from the gc later
![](img07.png)
### Generators
![](img08.png)
* just possible because stack frames are retained during function calles
* a generator function makes a new stack frame object with all the local variables
* * every time the function yields, that stack frame remembers that point so it can continue on the next iteration
# multithreading
![](img08.png)
* see: module asyncio
* functions sleep, they take no ressources
* the stack frame object keeps track of where to retrun to in our task
# decorators
![](img09.png)
* the call to the decorator returns a newly decorated or wrapped function based on the program code that was f bound to
* the user still calls f() - the original function - but they called the edited function

# Seeing this in practice
* showcases in a jupyter notbook (coming in some days)
* using `nbtutor` to see the python internals

