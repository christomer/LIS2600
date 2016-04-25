**Python** is a widely used high-level, general-purpose, interpreted, dynamic programming language. Its design philosophy emphasizes code readability, and its syntax allows programmers to express concepts in fewer lines of code than would be possible in languages such as C++ or Java]. The language provides constructs intended to enable clear programs on both a small and large scale.

Python supports multiple programming paradigms, including object-oriented, imperative and functional programming or procedural styles. It features a dynamic type memory management and has a large standard library.

Python interpreters are available for installation on many operating systems, allowing Python code execution on a wide variety of systems. Using third-party tools, such as Py2exe or Pyinstaller, Python code can be packaged into stand-alone executable programs for some of the most popular operating systems, allowing the distribution of Python-based software for use on those environments without requiring the installation of a Python interpreter. CPython, the reference implementation of Python, is free and open-source software and has a community-based development model, as do nearly all of its alternative implementations. (CPython is managed by the non-profit Python Software Foundation.)

### Using the Python Interpreter

The Python interpreter is usually installed as `/usr/local/bin/python3.5` on those machines where it is available; putting `/usr/local/bin`in your Unix shell’s search path makes it possible to start it by typing the command:

```c
$ `python 3.5`
```

Typing an end-of-file character (`Control-D` on Unix, `Control-Z` on Windows) at the primary prompt causes the interpreter to exit with a zero exit status. If that doesn’t work, you can exit the interpreter by typing the following command: `quit()`.

When invoking Python, you may specify any of these options:

```c
python [-bBdEhiIOqsSuvVWx?] [-c command | -m module-name | script | - ] [args]
```

The most common use case is, of course, a simple invocation of a script:

```c
python myscript.py
```

The interpreter’s line-editing features include interactive editing, history substitution and code completion on systems that support readline. Perhaps the quickest check to see whether command line editing is supported is typing `Control-P` to the first Python prompt you get. If it beeps, you have command line editing. If nothing appears to happen, or if `^P` is echoed, command line editing is not available, and you’ll only be able to use backspace to remove characters from the current line.

The interpreter operates somewhat like the Unix shell: when called with standard input connected to a `tty` device, it reads and executes commands interactively; when called with a file name argument or with a file as standard input, it reads and executes a *script* from that file.

A second way of starting the interpreter is `python -c command [arg] ...`, which executes the statement(s) in *command*, analogous to the shell’s `-c` option. Since Python statements often contain spaces or other characters that are special to the shell, it is usually advised to quote *command* in its entirety with single quotes.

Some Python modules are also useful as scripts. These can be invoked using `python -m module [arg] ...`, which executes the source file for *module* as if you had spelled out its full name on the command line. When a script file is used, it is sometimes useful to be able to run the script and enter interactive mode afterwards. This can be done by passing `-i` before the script.

An interface option terminates the list of options consumed by the interpreter, all consecutive arguments will end up in [`sys.argv`](https://docs.python.org/3/library/sys.html#sys.argv "sys.argv") – note that the first element, subscript zero (`sys.argv[0]`), is a string reflecting the program’s source.

`-c`` <command>`[](https://docs.python.org/3/using/cmdline.html#cmdoption-c "Permalink to this definition")

Execute the Python code in *command*. *command* can be one or more statements separated by newlines, with significant leading whitespace as in normal module code.

If this option is given, the first element of [`sys.argv`](https://docs.python.org/3/library/sys.html#sys.argv "sys.argv") will be `"-c"` and the current directory will be added to the start of [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path")(allowing modules in that directory to be imported as top level modules).

`-m`` <module-name>`[](https://docs.python.org/3/using/cmdline.html#cmdoption-m "Permalink to this definition")

Search [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path") for the named module and execute its contents as the [`\_\_main\_\_`](https://docs.python.org/3/library/__main__.html#module-__main__ "__main__: The environment where the top-level script is run.") module.

Since the argument is a *module* name, you must not give a file extension (`.py`). The module name should be a valid absolute Python module name, but the implementation may not always enforce this (e.g. it may allow you to use a name that includes a hyphen).

Package names (including namespace packages) are also permitted. When a package name is supplied instead of a normal module, the interpreter will execute `\<pkg\>.\_\_main\_\_` as the main module. This behaviour is deliberately similar to the handling of directories and zipfiles that are passed to the interpreter as the script argument.

If this option is given, the first element of [`sys.argv`](https://docs.python.org/3/library/sys.html#sys.argv "sys.argv") will be the full path to the module file (while the module file is being located, the first element will be set to `"-m"`). As with the [`-c`](https://docs.python.org/3/using/cmdline.html#cmdoption-c) option, the current directory will be added to the start of [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path").

Many standard library modules contain code that is invoked on their execution as a script. An example is the [`timeit`](https://docs.python.org/3/library/timeit.html#module-timeit "timeit: Measure the execution time of small code snippets.") module:

    python -mtimeit -s 'setup here' 'benchmarked code here'
    python -mtimeit -h \# for details

Read commands from standard input ([`sys.stdin`](https://docs.python.org/3/library/sys.html#sys.stdin "sys.stdin")). If standard input is a terminal, [`-i`](https://docs.python.org/3/using/cmdline.html#cmdoption-i) is implied.

If this option is given, the first element of [`sys.argv`](https://docs.python.org/3/library/sys.html#sys.argv "sys.argv") will be `"-"` and the current directory will be added to the start of [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path").

`<script>`

Execute the Python code contained in *script*, which must be a filesystem path (absolute or relative) referring to either a Python file, a directory containing a `\_\_main\_\_.py` file, or a zipfile containing a `\_\_main\_\_.py` file.

If this option is given, the first element of [`sys.argv`](https://docs.python.org/3/library/sys.html#sys.argv "sys.argv") will be the script name as given on the command line.

If the script name refers directly to a Python file, the directory containing that file is added to the start of [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path"), and the file is executed as the [`\_\_main\_\_`](https://docs.python.org/3/library/__main__.html#module-__main__ "__main__: The environment where the top-level script is run.") module.

If the script name refers to a directory or zipfile, the script name is added to the start of [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path") and the `\_\_main\_\_.py` file in that location is executed as the [`\_\_main\_\_`](https://docs.python.org/3/library/__main__.html#module-__main__ "__main__: The environment where the top-level script is run.") module.