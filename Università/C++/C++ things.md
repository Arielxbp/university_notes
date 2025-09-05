___

When a function is called, all of the parameters of the function are created as variables, and the value of each of the arguments is copied into the matching parameter (using copy initialization). This process is called <font style="color:salmon">pass by value</font>. Function parameters that utilize pass by value are called value parameters.

___

When a function parameter exists but is not used in the body of the function, do not give it a name. You can optionally put a name inside a comment.

___

Local variables are destroyed in the opposite order of creation at the end of the set of curly braces in which it is defined (or for a function parameter, at the end of the function).

___

If the object is a class type object, prior to destruction, a special function called a destructor is invoked. In many cases, the destructor does nothing, in which case no cost is incurred.

___

A forward declaration allows us to tell the compiler about the existence of an identifier before actually defining the identifier.

In the case of functions, this allows us to tell the compiler about the existence of a function before we define the function’s body. This way, when the compiler encounters a call to the function, it’ll understand that we’re making a function call, and can check to ensure we’re calling the function correctly, even if it doesn’t yet know how or where the function is defined.

To write a forward declaration for a function, we use a function declaration statement (also called a function prototype). The function declaration consists of the function’s return type, name, and parameter types, terminated with a semicolon. The names of the parameters can be optionally included. The function body is not included in the declaration.

___

A namespace provides another type of scope region (called namespace scope) that allows you to declare names inside of it for the purpose of disambiguation. Any names declared inside the namespace won’t be mistaken for identical names in other scopes.

std is a namespace

The :: symbol is an operator called the scope resolution operator. The identifier to the left of the :: symbol identifies the namespace that the name to the right of the :: symbol is contained within. <font style="color:salmon">If no identifier to the left of the :: symbol is provided, the global namespace is assumed</font>.

So when we say std::cout we’re saying “the cout that is declared in namespace std“.

This is the safest way to use cout, because there’s no ambiguity about which cout we’re referencing (the one in the std namespace).

___

Preprocessor

\#include


\#define directive can be used to create a macro.

A macro is a rule that defines how input text is converted into replacement output text.

There are two basic types of macros: object-like macros, and function-like macros.

Function-like macros act like functions, and serve a similar purpose. Their use is generally considered unsafe, and almost anything they can do can be done by a normal function.

Object-like macros can be defined in one of two ways:
\#define IDENTIFIER
\#define IDENTIFIER substitution_text

```cpp
#include <iostream>

#define MY_NAME "Alex"

int main(){
    std::cout << "My name is: " << MY_NAME << '\n';

    return 0;
}

/*
 *The preprocessor converts the above into the following:
 */

// The contents of iostream are inserted here

int main()
{
    std::cout << "My name is: " << "Alex" << '\n';

    return 0;
}
```

___

Header with fileName.h

Header files allow us to put declarations in one location and then import them wherever we need them. This can save a lot of typing in multi-file programs.

Source files should \#include their paired header file (if one exists). (like add.h with add.cpp)

Avoid \#including .cpp files.

You’re probably curious why we use angled brackets for \<iostream>, and double quotes for "add.h". It’s possible that a header file with the same filename might exist in multiple directories. Our use of angled brackets vs double quotes helps give the preprocessor a clue as to where it should look for header files.

When we use angled brackets, we’re telling the preprocessor that this is a header file we didn’t write ourselves. The preprocessor will search for the header only in the directories specified by the "include directories"(directories containing the header files that come with your compiler and/or OS).

When we use double-quotes, we’re telling the preprocessor that this is a header file that we wrote. The preprocessor will first search for the header file in the current directory. If it can’t find a matching header there, it will then search the "include directories".

___

To maximize the chance that missing includes will be flagged by compiler, order your \#includes as follows:

1. The paired header file
2. Other headers from your project
3. 3rd party library headers
4. Standard library headers

The headers for each grouping should be sorted alphabetically (unless the documentation for a 3rd party library instructs you to do otherwise).

___

- Always include header guards (we’ll cover these next lesson).
- Do not define variables and functions in header files (for now).
- Give a header file the same name as the source file it’s associated with (e.g. grades.h is paired with grades.cpp).
- Each header file should have a specific job, and be as independent as possible. For example, you might put all your declarations related to functionality A in A.h and all your declarations related to functionality B in B.h. That way if you only care about A later, you can just include A.h and not get any of the stuff related to B.
- Be mindful of which headers you need to explicitly include for the functionality that you are using in your code files, to avoid inadvertent transitive includes.
- A header file should \#include any other headers containing functionality it needs. Such a header should compile successfully when \#included into a .cpp file by itself.

___

Header guards are used for protection against when two header may have the same functions.
( Is like a singleton pattern, given a variable, it checks whether it is already \#defined, if not then if defines it and the header functions normally, so including the functions, but if it is already defined then it doesn't include the functions inside the header)
```cpp
#ifndef SOME_UNIQUE_NAME_HERE
#define SOME_UNIQUE_NAME_HERE

// your declarations (and certain types of definitions) here

#endif
```

In large programs, it’s possible to have two separate header files (included from different directories) that end up having the same filename (e.g. directoryA\config.h and directoryB\config.h). If only the filename is used for the include guard (e.g. CONFIG_H), these two files may end up using the same guard name. If that happens, any file that includes (directly or indirectly) both config.h files will not receive the contents of the include file to be included second. This will probably cause a compilation error.

Because of this possibility for guard name conflicts, many developers recommend using a more complex/unique name in your header guards. Some good suggestions are a naming convention of PROJECT_PATH_FILE_H, FILE_LARGE-RANDOM-NUMBER_H, or FILE_CREATION-DATE_H.

___

When printing information for debugging purposes, use std::cerr instead of std::cout. One reason for this is that std::cout may be buffered, which means there may be a pause between when you ask std::cout to output information and when it actually does.

___

Plog for debugging using a txt file for outputting error in text

___

float
double
long double
bool
char
int
long int
std::nullptr_t
void

___

When using floating point literals, always include at least one decimal place (even if the decimal is 0). This helps the compiler understand that the number is a floating point number and not an integer.

Note that by default, floating point literals default to type double. An `f` suffix is used to denote a literal of type float.

____

There is Nan -> 0 / 0 gives 1.#IND
There is Inf -> 5 / 0 gives 1.#INF

___

bool type are actually integer 0 or 1

true == 1

false == 0

printing bools using std::cout will print integer 1 or 0

to print using std::cout True or false use before printing:
std::cout << std::boolalpha; (to activate)
std::cout << std::noboolalpha; (to deactivate)

to input a bool using "true" or "false" (case sensitive) use before asking input:
std::cin >> std::boolalpha;

non-zero values get converted to Boolean _true_, and zero-values get converted to Boolean _false_.

___

Even though it is called a conversion, a type conversion does not actually change the value or type of the value being converted. Instead, the value to be converted is used as input, and the conversion results in a new value of the target type (via direct initialization).

___

Whenever you see C++ syntax (excluding the preprocessor) that makes use of angled brackets (<>), the thing between the angled brackets will most likely be a type. This is typically how C++ deals with code that need a parameterized type.

To perform an explicit type conversion, in most cases we’ll use the static_cast operator.
```cpp
static_cast<new_type>(expression)

print(static_cast<int>(5.5));

```

___
