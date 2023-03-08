DEBUG ?= 1
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

CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cpp)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

all: create build

create:
	@mkdir -p build

build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $^ $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

execute:
	@./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	@rm -rf $(BUILD_DIR)


$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@


.PHONY: all create build execute clean
