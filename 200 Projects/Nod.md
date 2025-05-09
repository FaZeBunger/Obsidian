#Programming #Programming/Language #Project/Nod

### Description

Nod is a compiled programming language meant to be extremely simple and built from the ground up. An interpreted language would have been easier, but a compiled language is more fun. 

### Parts
This project needs a [[Lexer]], which simply parses the file into tokens, [[Syntax Analyzer]] which turns the token sequence into an abstract syntax tree. After that, we have to do something called [[Semantic Analysis]], which creates a Semantic Graph. Finally, after that, we can begin to convert the language into assembly, by first creating an intermediate code representation, and then converting that into assembly. 

### Next Steps
- [ ] Create a Lexer
- [ ] Create a program to make a syntax tree
- [ ] Create a program for semantic analysis

