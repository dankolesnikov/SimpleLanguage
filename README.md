# Simple Language
> Programming language interpreter, similar to Scala subset

## Description

A programming language interpreter developed in Programming Paradigma class with Professor Cay Horstmann at SJSU.
Simple Language is similar to Scala subset but differs several ways:

* Only two types: integer and functions
* Defs end with semicolons
* Block has a single expression
* Function literals have syntax `{ ident, ident, ... => block }`
* `if` fakes `Boolean` similar to C: > 0 is true, <= 0 is false

## Grammar

	block ::= (valdef | fundef)* expr<br />
	expr ::= expr2 | "if" "(" expr ")" block "else" block <br />
	expr2 ::= term (( "+" | "-" ) term)* <br />
	term ::= factor (( "*" | "/" ) factor)* <br />
	factor ::= wholeNumber | "(" expr ")" | ident | funcall | funliteral <br />
	funcall ::= ident "(" (expr ("," expr)*)? ")" <br />
	funliteral ::= "{" (ident ("," ident)*)? "=>" block "}" <br />
	valdef ::= "val" ident "=" expr ";" <br />
	fundef ::= "def" ident "=" funliteral ";" 

## Examples 

Simple addition and multiplication

	val a = 1;
	val b = 6;
	a * a + b * b
	
Function literal

	val max = { x, y => if (x - y) x else y };

Higher-order function

	val twoTimes = { f, x => f(f(x)) }; 
	twoTimes({x => x * x}, 2)
	
Recursion

	def fac = { x => if (x) x * fac(x - 1) else 1 };

**Curry**

Multiplication

	val multiply = { x => { y => x * y } } ;
	multiply(3)(4)

Lists:

	val list = 1 :: 2 :: Nil;
	val y = isEmpty(list);
	val x = head(1 :: Nil);

### Credits

[Cay Horstmann](http://horstmann.com/), SJSU
