# CC: Program for compiling C programs; default cc
# CXX: Program for compiling C++ programs; default g++
# CFLAGS: Extra flags to give to the C compiler
# CXXFLAGS: Extra flags to give to the C++ compiler
# CPPFLAGS: Extra flags to give to the C preprocessor
# LDFLAGS: Extra flags to give to the linker

# conditions

# check if a variable is empty
# strip() function remove all whitespace
# ifeq ((strip(VAR)),)

# check if a variable is defined
# ifdef VAR

# Compiler Flags
# Debug: -g
# Release: -O0 -O1 -O2 -O3 -Og
# Includes: -I
# Warnings: -Wall -Wextra -Wpedantic -Wconversion



DEBUG ?= 1 # ?= user can change this variable
EXECUTABLE_NAME ?= main
ENABLE_WARNINGS ?= 1
CXX_STANDARD ?= c++20
CXX ?= g++

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

ifeq ($(ENABLE_WARNINGS), 1)
	CXX_WARNINGS = -Wall -Wextra -Wpedantic
else
	CXX_WARNINGS =
endif

CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
INCLUDE_FLAGS  = -I $(INCLUDE_DIR)
LDFLAGS =

ifeq ($(DEBUG), 1)
	CXXFLAGS += -g -O0
else
	CXXFLAGS += -O3
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(INCLUDE_FLAGS)

CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cpp) # create list of targets
# change directory and extension of the all files in the list
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

all: create build


create:
	@mkdir -p build # @ don't show this command in the terminal

build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	#rm $(BUILD_DIR)/*.o
	#rm $(BUILD_DIR)/$(EXECUTABLE_NAME)
	rm -r $(BUILD_DIR)


# $@: the file name of the target
# $<: the name of the first ependency
# $^: the names of all prerequisites


# for all source files, take file and compile him
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@

.PHONY: all create build execute clean # it's not files
