# Based Coding Standard

Our coding guide;
mostly for C/C++.

> [!NOTE]
> The most important thing is to be consistent with an existing codebase,
> don't make unnecessary large changes.

## Quick points ##
+ Keep a line width of 80
+ Never drop brackets
+ String NULL termination is spelled '\0', not '\00'
+ use NULL not 0, when applicable
+ Indent with 4 spaces
+ Try not to go over 4 levels
+ Use the correct editor

## Naming ##
+ Prefer US spelling when ambigous (color)
+ snake\_case\_for\_all symbols
+ kebab-case for files

---

## C/C++ specific ##

### Compilation ###
+ Provide a Makefile
+ Must not take more than one manual step

### Headers ###
+ NEVER use relative paths
+ Use K&R header guards

### Macros ###
+ Parenthesize macro values

### Padding ###
+ Pad after commas
+ Add padding around if, while, and for clauses
+ Do not pad after a function name `func()`, NEVER `func ()`
+ Do not pad inside parentheses `func(a)`, NEVER `func( a )`
+ Pad inside brackets always `{ ...; }`
+ Pad around operators

### Declaration ###
+ For functions always abide [static|extern] [inline] [type]
+ Put pointers in the center `char * abc`
+ Function parameters should remain on the same line... `func (int a) {...`
+ If a function has way too many parameters (line length greater than limit),
  format them into a block or lay them out in a indented list
+ Align adjacent declarations horizontally
+ Always typedef structs and enums, avoid `struct mytype myvar;` if possible
+ You may use anonymous structures

### Conditionals ###
+ align like this:
```c
    if (!a
    &&   b
    &&  !c) {
    ...
    }
```
+ avoid useless comparison information
```c
    if (a != 0) /* BAD */
    if (a) /* as god intended */
```

### Switch ###
+ Multi-line
```c
    switch (...) {
        case ...: {
            ...
        } break;
    }
```
 + Single line (if you dare)
```c
    switch (...) {
        case ...: ...; break;
    }
```

### Loops ###
+ Try to use the alphabetical iterators `i, j, k, ...`, try not to use more than three iterators
+ Use `while (true)` for infinite loops

### Operators ###
+ Use prefix increment by default `++i`

### Parenthesizing ###
+ Do not parenthesize return statements

### Naming ###
+ Use the POSIX reserved \_t suffix for new types

### Compilation ###
+ Resolve All Feasible Warnings given by selected compilers
   `clang -Weverything`
   `gcc -Wall -Wextra -Pedantic`
+ Consider tools like splint, but don't break your back over it

### The Dreaded Multi-line Comment ###
+ Don't ever use them unless you have to

   C++ comments for logical separation and small comments

   C comments for large explanation
+ Use them always and vanish C++ demons from your code
+ Use `#if 0... #endif /* 0 */` if you want to comment out blocks of code

### Loops ###
+ If you will have NO other use for an iterator, put it inside the for loop declaration, C99> style
+ Avoid commas in conditionals, it'll make Xolatile seethe
