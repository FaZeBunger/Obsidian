---
aliases:
  - RDP
tags:
  - Programming
  - Programming/Algorithms
---
### Description

Recursive Descent Parsing basically allows us to mimic grammar rules by defining what grammar rules we are following and having them recursively call each other, consume tokens, or give a syntax error.

Of course, this is a very basic description, and the actual process is easier to show rather than explain.

### Implementation

We will start with a simple implementation of 3 different operations. 
1. Assign a variable
2. Add two terms together
3. Subtract one term from another

For this very basic example, we will have 4 functions `parse_program`, `parse_statement`, `parse_expression`, and `parse_term`. Now lets define what a `program`, `statement`, `expression`, and `term` are.
1. `program` - one statement followed by a semicolon.
2. `statement` - an identifier followed by an equals sign, followed by an expression.
3. `expression` - a `term`, optionally followed by one or more `+` or `-` operators and more `term(s)`. This handles `a + b - c`.
4. `term` - either an identifier or a number. 

For this simple case, terms are the basic building blocks. For larger more complex languages with more operations and tools, you would have more than one basic building block.

1. `parse_program`:
	- Calls `parse_statement()` to get the [[Abstract Syntax Tree|AST]] node for the statement. 
	- Checks if the next token is a `SEMICOLON`. If yes, consume it. If no, report error. 
	- Returns the statements [[Abstract Syntax Tree|AST]] node as the root.
2. `parse_statement()`:
	- Checks for `IDENTIFIER`. If yes, consume, create `Variable` [[Abstract Syntax Tree|AST]] node (left side of assignment). If no, report error. 
	- Checks for `ASSIGN (=)`. If yes, consume. If no, report error. 
	- Calls `parse_expression()` to get the [[Abstract Syntax Tree|AST]] node for the value (right side of the assignment). 
	- Creates `Assignment` [[Abstract Syntax Tree|AST]] node, linking the variable node and the expression node as children. 
	- Returns the `Assignment` [[Abstract Syntax Tree|AST]] node. 
3. `parse_expression()`:
	- First, parse the initial `term` by calling `parse_term()`. Let's call the resulting [[Abstract Syntax Tree|AST]] node `left_operand_node`.
	- **Loop**: While the current token is either `PLUS` or `MINUS`.
		- Get the `operator_type` (`ADD` or `SUBTRACT`) from the current token.
		- Consume the `PLUS` or `MINUS` token.
		- Call `parse_term()` again to get the right-hand side [[Abstract Syntax Tree|AST]] node for the operation. Let's call it `right_operand_node`.
		- Create a new [[Abstract Syntax Tree|AST]] node for the operation (`Add` or `Subtract`), with `left_operand_node` as its left child and `right_operand_node` as its right child.
		- **Crucially**, update `left_operand_node` to be this newly created operation node. This handles changing operations (like `a + b - c`).
	- When the loop finishes (the next token is not `+` or `-`), return the final `left_operand_node` (which is now the root of the expression's AST).
4. `parse_term`: 
	- Looks at the current token. 
	- If it's an `IDENTIFIER`, consume it, create `Variable` [[Abstract Syntax Tree|AST]] node, return it. 
	- If it's a `NUMBER`, consume it, create `Literal` [[Abstract Syntax Tree|AST]] node, return it. 
	- If it's neither, report error.

Let's look at an example `result = a + 10 - b;`
We'll focus on just the portion for `a + 10 - b`
- Start `parse_expression()`. 
- Calls `parse_term()`. `parse_term()` sees `IDENTIFIER a`, consumes it, returns `Variable(a)` node. `left_operand_node` is `Variable(a)`. 
- Current token is `PLUS`. Enter loop.
	- `operator_type` is `ADD`. Consume `PLUS`.
	- Call `parse_term()`. `parse_term` sees `NUMBER 10`, consumes it, returns `Literal(10)` node. `right_operand_node` is `Literal(10)`.
	- Create `Add` node. Left child: `left_operand_node` (`Variable(a)`) . Right child: `right_operand_node` (`Literal(10)`). New node is `Add(Variable(a), Literal(10)`. 
	- Update `left_operand_node` to this new `Add` node. `left_operand_node` is now `Add(Variable(a), Literal(10))`. 
	- Current token is `MINUS`. Enter loop.
		- `operator_type` is `Subtract`. Consume `MINUS`. 
		- Call `parse_term()`. `parse_term()` sees `IDENTIFIER b`, consumes it, returns `Variable(b)` node. `right_operand_node` is `Variable(b)`. 
		- Create `Subtract` node. Left child: `left_operand_node` (`Add(Variable(a), Literal(10))`).  Right child: `right_operand_node` (`Variable(b)`). New node is `Subtract(Add(Variable(a), Literal(10)), Variable(b))`. 
		- Update `left_operand_node` to this new `Subtract` node. `left_operand_node` is now `Subtract(Add(Variable(a), Literal(10)), Variable(b))`. 
	- Current token is `SEMICOLON`. Loop condition fails (not `PLUS` or `MINUS`). 
	- `parse_expression()` returns `left_operand_node`, which is `Subtract(Add(Variable(a), Literal(10)), Variable(b))`.

The [[Abstract Syntax Tree|AST]] structure for the expression `a + 10 - b`.

```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2025.4.23 - 20.12pm.drawing",
	"width": 752,
	"aspectRatio": 2.301307124473716
}
```
