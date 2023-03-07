##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first ependency
# $^: the names of all prerequisites

DEBUG = 1
EXECUTABLE_NAME = main

CXX_STANDARD = c++20
CXX = g++
CXX_WARNINGS = -Wall -Wextra -Wpedantic

CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS =

ifeq ($(DEBUG), 1)
	CXXFLAGS += -g -O0
else
	CXXFLAGS += -O3
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS)

CXX_SOURCES = $(wildcard *.cpp)
CXX_OBJECTS = $(patsubst %.cpp, %.o, $(CXX_SOURCES))

build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)

execute:
	./$(EXECUTABLE_NAME)

clean:
	rm *.o
	rm $(EXECUTABLE_NAME)

%.o: %.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@
