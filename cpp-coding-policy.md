# File structure, naming, etc.

* All classes should generally live in their own file, named ClassName.cpp.
* For particularly large classes, major subsystems may be split up into their own files named ClassName_subsystem.cpp.
For example, Foo_rendering.cpp and Foo_events.cpp.
* Trivial helper classes/structures may be declared in the associated ClassName.h.
* All headers should have include guards, with a macro named ClassName_h.
* All files should begin with the project standard license header, then a Doxygen `@file` comment.

# API Usage

* Prefer use of logtools calls over raw `printf()` / `std::cout` for printing log messages with proper filtering etc.
* Use `new` / `delete` for memory allocation rather than C-style `malloc()` / `free()`.
* All string functions that do not take an explicit buffer size argument are forbidden. This includes but is not
limited to `gets()`, `strcpy()`, `sprintf()`, etc.
* Use of C string manipulation functions with an explicit size, such as `snprintf()`, is acceptable.
* Field width specifiers are required on all `sscanf()` calls that write to strings. For example, `%30s` rather than
`%s`.

# Global Variables

* Use global variables only when there is no other practical way to accomplish the task.
* Prefix all global variables with g_ to avoid namespace conflicts with local or member variables.

# Classes

* Use CamelCase naming without a leading C. For example, `FoobarWindow`, not `CFoobarWindow` or `foobarWindow`.
* Internal implementation details should be `protected` to the extent practical to provide a clean API boundary.
* Minimize use of `private` members in classes likely to be used as bases for other classes.
* Prefix all member variables with m_ to avoid namespace conflicts with local or global variables.
* Use CamelCase naming with an initial lowercase for member variables. For example `m_sampleRateLabel`.
* When declaring user interface objects such as GTK elements, indent according to the UI element hierarchy.

# Formatting

* One level of indentation = one \t character = four columns. Do not use spaces for indentation.
* Curly braces go on their own line.
* Curly braces are not required for a control statement with a single-line body, however if an explicitly empty body is
used then use braces rather than simply a semicolon. The opening and closing braces may be on the same line.
* The * in a pointer declaration is part of the type, not the variable. For example `int* foo`, not `int *foo`.
* Do not put a space between a keyword or identifier name and an opening parentheses. For example `if(foo)`, not `if
(foo)`.
* If order of operations is not trivially obvious by inspection, add additional parentheses. Place spaces between
multiple levels of parentheses. For example `if( (foo == bar) || (baz == foobar) )`.

* [astyle](https://sourceforge.net/projects/astyle/) code formatting (for *.cpp)
`astyle -T --indent-switches --style=bsd --lineend=linux`
