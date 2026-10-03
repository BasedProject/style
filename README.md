# Based Coding Standard

Our coding guide;
mostly for C/C++.

> [!NOTE]
> The most important thing is to be consistent with an existing codebase;
> don't make unnecessary large changes.

## Quick points ##
+ Keep a line width of 80
+ Indent with 4 spaces
+ Try not to go over 4 levels of indentation
+ Use the correct editor

## Naming ##
+ Prefer US spelling when ambiguous (color)
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
+ Prefer `*_IMPLEMENTATION` in header-only libraries

### Compilation ###
+ Resolve All Feasible Warnings given by selected compilers
   `clang -Weverything`
   `gcc -Wall -Wextra -Pedantic`
+ Consider tools like splint, but don't break your back over it

### Macros ###
+ Parenthesize macro values

### Padding ###
+ Pad after commas
+ Add padding around if, while, and for clauses
+ Do not pad after a function name `func()`, NEVER `func ()`
+ Do not pad inside parentheses `func(a)`, NEVER `func( a )`
+ Pad inside brackets `{ ...; }`
+ Pad around operators

### Declaration ###
+ For functions always abide [static|extern] \n [inline] \n [type]
+ Put pointers in the center `char * abc`
+ Function parameters should remain on the same line... `func (int a) {...`
+ If a function or call has way too many parameters (line length greater than limit),
  put each on its own line and indent it:
```c
    void foo(
        int a,
        int b,
        int c
    ) {
        ;
    }
    // ---
    foo(
        a,
        b,
        c
    );
```
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
+ Try to use the conventional alphabetical iterators `i, j, k`
+ If alphabetical iterators are not expressive enough, use whole words
+ Use `while (true)` for infinite loops
+ If you will have NO other use for an iterator, put it inside the for loop declaration, C99> style
+ Avoid commas in conditionals, it'll make Xolatile seethe

### Operators ###
+ Use prefix increment by default (`++i`)

### Parenthesizing ###
+ Do not parenthesize return statements
+ Always parenthesize macro arguments
+ Never drop brackets
+ Use `while (0)` for creating arbitrary scopes;
   highly preferred in gamedev code to segment code,
   instead of over DRY-ing volatile code

### Naming ###
+ Use the POSIX reserved `_t` suffix for new types
+ Use the `_e` suffix for enums
+ Use the `_u` suffix for unions

### Literals ###
+ String NULL termination is spelled '\0', not '\00'
+ Use NULL not 0, when applicable
+ Prefer C23 int literal sectioning
+ Prefer true and false for booleans

### Comments ###
+ Use (single line) C comments to partition code (`// Init`)
+ Use (multi line) C++ comments with leading starts to explain sections of code
+ Use `#if 0... #endif` if you want to comment out blocks of code
+ "This is a bridge" is not insigthful commentary
