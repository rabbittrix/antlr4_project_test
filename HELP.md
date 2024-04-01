# Getting ANTLR 4
Anyone who has ever tried to create a programming language knows the pain of creating a lexer and a parser, 
but did you know that there is a way to generate this part of the code by writing it to a file defining the 
grammar?
### Documentations

ANTLR currently supports Java, C#, Python 2 and 3, Go, C++, Swift, PHP and Dart

It can generate code for all these languages, but the official one and the one with the best integration is 
Java with Gradle/Maven, so that will be the language I will use in this post.

Furthermore, it has extensions for antlr .g4 files for intellij, eclipse and vscode, 
which in addition to providing syntax highlighting and a Language Server to check the code and show errors 
in the editor, it also has a window to test the grammar and show the Parse Tree of your code written in your 
language.

### Guides
The language in this example will be a stack-based language like Fortran:
function main in
    69 print
    35 34 + print
    69 96 swap print print
    70 dup print print
    2 2 + 4 = if
        "2 + 2 = 4, Cool" print
    end else
        "2 + 2 = 22?" print
    end
end

* Create a gradle project and add the antlr plugin and antlr runtime;
* Now you need to create a folder in src/main/antlr and create a grammar file;
* When you run Gradle's generateGrammarSource task, it will generate a parser and lexer that implements your grammar into the build folder, and will add it to the classpath.
  In your Main class you need to instantiate the lexer and the parser to generate the parse tree
* Now you need to create a visitor to visit the tree nodes and compile it into machine code or execute the code immediately
    * But then it's up to you :) I'll leave an example of my language;
* In my case, I convert data structures into data structures that are easier to work with, both to interpret and to compile, in fact, this is one of the things that programmers do a lot, transforming information into formats that are easier to work with.
* Now in Main you need to create a new visitor and call the visit method of the parent class passing the parse tree returned by antlr
* I decided to return a Program in the visit that has all the functions and properties of the program, but you can return whatever you want, just put in the generic of the parent class the type you want to return from all the visit methods of your class

### Additional Links

These additional references should also help you:

* implementation "org.antlr:antlr4-runtime:4.10.1"

* https://www.antlr.org/

