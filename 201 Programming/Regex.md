---
aliases:
  - Regular Expression
tags:
  - Programming
  - Programming/Algorithms
---
### Description

Regex (Regular Expression) is an incredibly powerful tool used for matching expressions. It is used in many areas of programming, especially lexical analysis ([[Lexer|Lexing/Tokenizing]]) for compilers/interpreters.

You could think of Regex as a flexible and fast way to search for patterns in text.

--- 

### What it does

Regex is a sequence of characters that defines a pattern. This pattern is used to find, match, or manage substrings within a larger body of text. You can use Regex to:
- **Validate** - Check if a string matches a specific format (e.g. a valid email address?, only digits?).
- **Find** - Locate occurrences of a pattern within a string (e.g. Find all phone numbers in a document).
- **Replace** - Locate occurrences of a pattern and replace them with something else.
- **Split** - Break a string into parts based on a pattern (though often handled by other string functions).

---

### How it works

You give a Regex engine a pattern (the regex string) and a target string (the text you want to search). The engine then compares the pattern against the target string character by character, or in sequences, according to the rules defined by the metacharacters in the pattern. It essentially tries to find if any part of the target string "fits the description" given by your regex pattern. 

--- 

### Basic Regex Syntax

Regex syntax uses a combination of literal characters and special characters called **metacharacters** that have special meanings. 
1. **Literal Characters:** Most characters simply match themselves.
	- `a` matches the character 'a'. 
	- `1` matches the character '1'. 
	- `=` matches the character '='. 
	- `hello` matches the exact sequence "hello". 
2. **Metacharacters (Special Meaning):** These give regex its power. 
	- `.` Matches **any single character** (except newline typically).
		- `a.b` matches "aXb", "a=b", "a3b", etc. 
	- `*` Matches the **preceding element zero or more times**
		- `a*` matches "", "a", "aa", "aaa", etc. 
		- `ab*c` matches "ac", "abc", "abbc", etc. 
	- `+` Matches the **preceding element one or more times**
		- `a+` matches "a", "aa", "aaa", etc. (But not "").
		- `ab+c` matches "abc", "abbc", "abbbc", etc. (But not "ac").
	- `?` Matches the **preceding element zero or one time**
		- `a?` matches "" or "a"
		- `colou?r` matches "color" or "colour".
	- `|` Acts like an **OR** operator. Matches either the element before or after the pipe. 
		- `cat|dog` matches either "cat" or "dog".
	- `()` **Groups** elements together so quantifiers (`*`, `+`, `?`) or `|` apply to the whole group. Also used to "capture" matched substrings.
		- `(ab)+` Matches "ab", "abab", "ababab", etc.
		- `(cat|dog)s` Matches "cats" or "dogs"
	- `[]` Defines a **character set**. Matches **any single character** that is inside the brackets.
		- `[abc]` Matches 'a', 'b', or' c'
		- `[0-9]` Matches any single digit 0 to 9.
		- `[a-z]` Matches any lowercase letter.
		- `[A-Z]` Matches any uppercase letter.
		- `[a-zA-Z]` Matches any letter.
	- `[^...]` Defines a **negated character set.** Matches any single character that is not in brackets.
		- `[^0-9]` Matches any single character that is not a digit.
	- `^` Matches the **beginning of a string** (or line depending on options).
		- `^abc` only matches "abc" if it's at the very start of the string.
	- `$` Matches the **end of a string** (or line depending on options).
		- `$xyz` only matches "xyz" if it's at the very end of the string.
	- `\` **Escapes** the following metacharacter, making it literal. Also used to create special character classes.
		- `\.` matches a literal dot `.`.
		- `\+` matches a literal plus `+`.
		- `\\` matches a literal backslash `\`.
	- **Special Character Classes (using `\`):** Common shortcuts for character sets.
		- `\d`: Matches any digit (equivalent to `[0-9]`).
		- `\w`: Matches a "word" character (letter, digit, or underscore; equivalent to `[a-zA-Z0-9_]`).
		- `\s`: Matches any whitespace character (space, tab, newline, etc.).
		- `\D`: Matches any **non**-digit (equivalent to `[^0-9]`).
		- `\W`: Matches any **non**-word character (equivalent to `[^a-zA-Z0-9_]`).
		- `\S`: Matches any **non**-whitespace character.