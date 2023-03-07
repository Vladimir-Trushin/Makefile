##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first ependency
# $^: the names of all prerequisites

DEBUG = 1
EXECUTABLE_NAME = main
INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CXX_STANDARD = c++20
CXX = g++
CXX_WARNINGS = -Wall -Wextra -Wpedantic

CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
INCLUDE_FLAGS  = -I $(INCLUDE_DIR)
LDFLAGS =

ifeq ($(DEBUG), 1)
	CXXFLAGS += -g -O0
else
	CXXFLAGS += -O3
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(INCLUDE_FLAGS)

CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cpp)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(CXX_SOURCES))



build: create $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	#rm $(BUILD_DIR)/*.o
	#rm $(BUILD_DIR)/$(EXECUTABLE_NAME)
	rm -r $(BUILD_DIR)

create:
	mkdir -p build

$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@
