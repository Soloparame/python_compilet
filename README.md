## Details
+ **Project Title:** Python Compiler 
	       - Using C language till Optimisation of Intermediate Code.
	       - Using Python Language for Target Code Generation.
+ **Team Members:**
  
  *1	[Bezawit Megersa]- [1405067] 
  *2	[Bezawit Mamo]	  -      [1405561] 
  *3	[Betelhem Tsega]   -	 [1404679]
  *4	[Afomiya Ketsella]  -     [ 1403952] 
  *5	[Afrah Maruf]	    -     [1405436] 
  *6	[Yordanos Molla]   -	[ 1411047]
  *7.	[Rebika Yhinew]     -	 [1405547]
  
   
   # commands we used to run
flex proj.l   to generate lex.yy.c file
bison -d proj1.y to generate y.tab.c, y.tab.h, proj1.tab.c and  proj1.tab.h
gcc lex.yy.c proj1.tab.c -o compiler
Get-Content inp.py | ./compiler  to generate compiler.exe                                    

+ # Python-Compiler
All phases of a compiler for Python Language have been implemented using C language. The constructs 'if-else' and 'while' have been handled.  
  
## Steps To Run
1) Install Flex (to make lex program work)
```
sudo apt-get upgrade
sudo apt-get install flex
```
2) Install Bison (to make yacc program work)
```
sudo apt-get upgrade
sudo apt-get install bison
```
3) Run the lex and yacc files
```
lex proj.l && yacc -d -v proj1.y && gcc lex.yy.c y.tab.c -ll -lm -w
```
4) Run the TargetCodeGenerator.c file
```
gcc -o TargetCodeGenerator .\TargetCodeGenerator.c
.\TargetCodeGenerator.exe
```  
## Details

## Introduction
The **_proj.l_** lex file and **_proj1.y_** yacc file work together to **parse** the Python code in the **_inp.py_** file and **generate tokens** to output a **symbol table** and create an **abstract syntax tree** and hence, generate the **optimised intermediate code**. This optimised intermediate code is saved in the file **_IntermediateCode.txt_** which is then accessed in the **_TargetCodeGenerator.c_** file. This file converts this optimised intermediate code to the **target code** for a hypothetic machine model which will be discussed further.  
  
File Descriptions
1. compiler.exe
Purpose:

The compiled executable file generated after combining the Lex and Yacc outputs.

Processes the input file (e.g., inp.py) to perform tokenization and generate a symbol table.

Usage:

Run this file with the input file to observe the tokenization and symbol table generation process.
2. inp.py
## Purpose:

A sample Python script provided as input for the lexer and parser.

Used to test the lexical analysis and parsing functionality.

Example:

A Python script containing identifiers, keywords, and operators.

3. lex.yy.c

## Purpose:
This file is generated when we run the command flex proj.l.

The C source file generated by Lex from proj.l.

Implements the lexical analysis logic, breaking the input into tokens based on rules defined in proj.l.

4. output.txt

## Purpose:

Stores the output generated by running a.out on inp.py.

Includes the list of identified tokens and the symbol table.

5. phase_1.png

## Purpose:

A diagram visualizing the workflow of the tokenization and symbol table generation phase.

Illustrates how the input is processed and transformed.

6. proj.l

## Purpose:

The Lex file defining the rules for tokenizing the input source code.

Contains patterns to match keywords, identifiers, literals, and operators.

Example Rule:

if { return IF; } matches the keyword if and returns the token IF.

7. proj1.y

## Purpose:

The Yacc file defining the grammar rules for parsing the tokenized input.

Builds a parse tree and generates the symbol table.

Example Rule:

stmt : IF expr THEN stmt defines a rule for an if statement.

8. y.tab.c

## Purpose:

The C source file generated by Yacc from proj1.y.

Implements the parsing logic as per the grammar rules.

9. y.tab.h

## Purpose:

The header file generated by Yacc, containing token definitions.

Ensures consistency between Lex and Yacc by defining token constants.

## Workflow

Lexical Analysis:

proj.l is processed by Lex to generate lex.yy.c.

lex.yy.c identifies tokens such as keywords, identifiers, literals, and operators from inp.py.

## Parsing:

proj1.y is processed by Yacc to generate y.tab.c and y.tab.h.

y.tab.c validates the syntax of the tokens and generates a parse tree.

## Compilation:

Both lex.yy.c and y.tab.c are compiled using a C compiler (e.g., gcc) to produce the a.out executable.

## Execution:

Running a.out with inp.py as input generates:

A list of tokens.

A symbol table, which is saved in output.txt.

## "How to Use"

Generate Lexer and Parser:

lex proj.l
yacc -d proj1.y
gcc lex.yy.c y.tab.c -o a.out

## "Run the Program:""

./a.out < inp.py > output.txt

View Results:

Tokens and symbol table will be in output.txt.

 Refer to phase_1.png for a visual explanation.
## Various folders
1) **1-Token_And Symbol_Table:** This folder contains the code that outputs the tokens and the symbol table.
2) **2-Abstract_Syntax_Tree:** This folder contains the code that displays the abstract syntax tree.
3) **3-Intermediate_Code_Generation:** This folder contains the code that generates the symbol table before optimisations and the intermediate code.
4) **4-Optimised_ICG:** This folder contains the code that generates the symbol table after optimisations, the quadruples table and the optimised intermediate code.
