#
# makefile for TINY
# GCC Version
#

CC = gcc

CFLAGS = 

LEX = flex

LFLAGS =

YACC = bison #doesn't work replacing this into the y.tab.c y.tab.h:

YFLAGS = --yacc --defines=y.tab.h #doesn't work replacing this into the y.tab.c y.tab.h:

OBJS = main.o util.o lex.yy.o y.tab.o symtab.o analyze.o code.o cgen.o 

tiny: $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o tiny -lfl

main.o: main.c globals.h util.h scan.h parse.h analyze.h cgen.h y.tab.h
	$(CC) $(CFLAGS) -c main.c

util.o: util.c util.h globals.h
	$(CC) $(CFLAGS) -c util.c

lex.yy.c: tiny.l y.tab.h
	$(LEX) $(LFLAGS) tiny.l

lex.yy.o: lex.yy.c scan.h util.h globals.h
	$(CC) $(CFLAGS) -c lex.yy.c

y.tab.c y.tab.h: tiny.y
	bison --yacc --defines=y.tab.h tiny.y

y.tab.o: y.tab.c parse.h scan.h globals.h util.h
	$(CC) $(CFLAGS) -c y.tab.c

symtab.o: symtab.c symtab.h
	$(CC) $(CFLAGS) -c symtab.c

analyze.o: analyze.c globals.h symtab.h analyze.h
	$(CC) $(CFLAGS) -c analyze.c

code.o: code.c code.h globals.h
	$(CC) $(CFLAGS) -c code.c

cgen.o: cgen.c globals.h symtab.h code.h cgen.h
	$(CC) $(CFLAGS) -c cgen.c



clean:
	-rm main.o
	-rm util.o
	-rm symtab.o
	-rm analyze.o
	-rm code.o
	-rm cgen.o
	-rm y.tab.c
	-rm y.tab.h
	-rm lex.yy.c
	-rm lex.yy.o
	-rm y.tab.o
	-rm tiny
	-rm tm

tm: tm.c
	$(CC) $(CFLAGS) tm.c -o tm


all: tiny tm

