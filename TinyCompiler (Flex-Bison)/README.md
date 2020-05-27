*Modified from the original*

The other files in the distribution are the source code files 
in standard C for the TINY compiler and Tiny Machine simulator
as described in the text:

	Compiler Construction - Principles and Practice, by Kenneth C. Louden,
	PWS Publishing Co., 1997.

They are (with very minor variations) all the files as listed in Appendices
B and C of the text.

At the top level are:

     The file you are now reading (README):

     The sixteen files as listed on page 23 of the text (which are
     used to make the TINY compiler)

     The tm.c source code file for the TM machine interpreter

     A Makefile for the TINY compiler and TM simulator.

This is the lex/Flex, Yacc/Bison version of the compiler.

For making changes to the language, you should change the files:

(Language modification)
-tiny.l
-tiny.y

(printing modified tokens in the Tiny Compiler)
-util.c

(code generation for the TM interpreter)
-cgen.c
-code.c (if you need more assembly-like instructions)

