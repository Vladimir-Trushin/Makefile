###############
## VARIABLES ##
###############
# Note: Variables can only be strings
# Note: Single or double quotes for variable names or values have no meaning to Make

# CC: Program for compiling C programs; default cc
# CXX: Program for compiling C++ programs; default g++
# CFLAGS: Extra flags to give to the C compiler
# CXXFLAGS: Extra flags to give to the C++ compiler
# CPPFLAGS: Extra flags to give to the C preprocessor
# LDFLAGS: Extra flags to give to the linker


DEBUG = 1
EXECUTABLE_NAME = main

CC = gcc
CFLAGS =

CXX_STANDARD = c++20
CXX_WARNINGS = -Wall -Wextra -Wpedantic
LDFLAGS =

CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)

ifeq ($(DEBUG), 1)
	CXXFLAGS += -g -O0
else
	CXXFLAGS += -O3
endif

build: main.o print_lib.o
	$(CXX) $(CXXFLAGS) main.o print_lib.o $(LDFLAGS) -o $(EXECUTABLE_NAME)

main.o:
	$(CXX) $(CXXFLAGS) main.cpp -c

print_lib.o:
	$(CXX) $(CXXFLAGS) print_lib.cpp -c

clean:
	rm *.o
	rm $(EXECUTABLE_NAME)