# Name: Shengtao Li
# Course: CS178 Build Automation for DevOps and QA
# CRN: 76718
# Date: 9/13/2017
# Assignment: Makefile for ServerCountThrees

#target
executable=ServerCountThrees

#required sources, objects, and datafile(s) for testing
datafile=./data/threesData.bin

# make convention to have default target be all
all: ServerCountThrees directories copy test

# default build for our executable
ServerCountThrees: ServerCountThrees.o readInt32BitLE.o
		gcc -o ServerCountThrees ServerCountThrees.o readInt32BitLE.o
ServerCountThrees.o: ./src/ServerCountThrees.c ./src/readInt32BitLE.h
		gcc -c ./src/ServerCountThrees.c -o ServerCountThrees.o
readInt32BitLE.o: ./src/readInt32BitLE.c ./src/readInt32BitLE.h
		gcc -c ./src/readInt32BitLE.c -o readInt32BitLE.o

# make directory build
.PHONY: directories

directories:
		mkdir -p build

# copy over data file and executables to build directory 
.PHONY: copy
copy: ${datafile} ${executable} directories
		cp ${datafile} ./build
		cp $(executable) ./build

# test the program

.PHONY: test
test: $(executable) $(datafile) copy directories
	cd build && ./$(executable)
#print a blank newline, slightly easier to read

#clean directory, using force remove to suppress no such file errors
.PHONY: clean
clean: 
	rm -f $(executable) $(objects)
	rm -rf ./build 
