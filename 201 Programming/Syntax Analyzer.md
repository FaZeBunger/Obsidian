---
aliases:
  - Syntactic Analyzer
  - Parser
tags:
  - Programming
  - Project/Nod
---

### Description

The Syntax Analyzer is what converts a series of [[Tokens]] into an [[Abstract Syntax Tree]].  It does this by using the formal grammar rules of the language it is parsing. The grammar rules define how tokens can be combined to form valid program constructs like expressions, statements, function definitions, etc. 

The Syntax Analyzer reads the stream of tokens and then attempts to match the sequence against the grammar rules. 

### Example

Take, for example, this python code: `x = 10 + y`.  
The [[Abstract Syntax Tree]] for this line of code would look as such:
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.4.23 - 18.26pm.drawing",
	"width": 693.333251953125,
	"aspectRatio": 2.4859007352941176
}
```

### Implementation 

To implement a program that can create this tree by using [[Recursive Descent Parsing]]. This algorithm allows us to mimic grammar rules by defining what grammar rules we are following and having them recursively call each other, consume tokens, or give a syntax error.













