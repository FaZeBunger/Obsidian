---
tags:
  - Programming/Language
  - Programming/Lexer
aliases:
  - Token
---
### Description

A token is the smallest part of a [[Compiler]]. Each token represents some thing in the code like a number, string, a name, left or right brackets, etc.

The point of the tokens is for the [[Lexer]] to read the file into a series of tokens, which is then converted into an [[Abstract Syntax Tree]] by the Parser.

---

### Example 

In a simple programming language like python, we could read a simple file like:
```python
print("Hello World")
```

We could convert the print command to a `print` token, the parentheses to their own tokens, and the string to it's own token and so on with other functions. 

This would then be read by the parser, and it would evaluate what the sequence of tokens is meant to do.

---

### Types

There are many different types of tokens, each for a different operation, symbol, or keyword. For example, there would be different types for `string`, `print`, `var`, `if`, `for`, `;`, `:` etc.

Each type of token classifies what operation that keyword does. 

---

### Implementation

Each Token holds two values, its type and some value. For some tokens the value will be none. For example, if you had a `string` token, it would hold the contents of the string it was created from, but for tokens like `;` or `:`, these would only have the token for the type of punctuation that it is, and would not hold a value inside of it, thus its value would be None.

```c++
enum struct TokenType {
	Print,
	String, 
	Bool,
	LeftBracket,
	RightBracket,
	IDENTIFIER,
	Operation,
}

class Token {
	TokenType type;
	std::variant<std::string, bool, int, std::monostate> value;
}
```

This is a simple implementation in `C++` for a Token that can hold both a type and a value. In a language like `rust` though, an `enum` has the ability to hold a value, and you would not need to implement this feature. 












