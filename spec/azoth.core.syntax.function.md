## Declaring functions

Ok. Its simple. In programming theory we have two types of subroutines: procedures and function. Procedure does not return anything but function does. For performance reasons system programmers can require no return actions to save CPU time. For that reason there are two keywords: `proc` and `func`. Function does not require return statement as last expression in function body is considered as result. For simple functions its means nothing but it will help more complex systax constructs.

Return type is deduced from return expression. But if programmer want some automatic type casts of returned value or make compiler more restrictive for function usage he can write return type after argument list. 

Function declaration code looks like this:
```
func myFunc (t: Struct, agr2 -> Float):
    t.a = 42
    t.e
```

Equivalent C code:
```
float myFunc (struct Struct t, /*deduced when used*/ arg2) {
    t.a = 42;
    return t.e;
}
```

## Calling function
Calling fucntion is easy. Like in other languages you write `var1 = func1(arg1, arg2)`. Left is variable that gets function result then goes function name and then there are two arguments in parentheses. 

There are two more ways to call fucntion of proc. First additional syntax is designed to be fuctional programming friendly: `var1 = func1 arg1 arg2`. You easy can see that we just dropped punctuation symbols.

Second one is also easy to understand but more trickier. Same call as above: `var1 = arg1.func1(arg2)`. There are some purposes for this.
* this type of calling will help implement OOP style in Azoth lang
* it gives good support for type methods extension (that situations where you can't edit someone else's code)
* this gives possibility to implement basic simple principle in language: there are only two base primitive entities: data and fucntions to process data.

We can mix first and second additional styles: `var1 = arg1 fucn1 arg2`. Why this? It's a support for implementation of "basic simple principle in language". Unlike C++, C# or others there are no special "operator" functions, they are just simple binary fucntions. Here's example:
```
// declare operator:
func * (m: Matrix, v: Vector -> Matrix):
    ... //  <--implementation goes here
    return res

// usage:
val m1 = createMatrix  // <- this is function call: createMatrix()
val v1 = newVec 1.0    // <- also func call: newVec(1.0)
val vRes = m1 * v1     // <- here we call our declared example func *(m1, v1)
```