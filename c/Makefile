DEBUG ?= 1
EXECUTABLE_NAME ?= main
ENABLE_WARNINGS ?= 1
C_STANDARD ?= c17
CC ?= gcc

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

ifeq ($(ENABLE_WARNINGS), 1)
	C_WARNINGS = -Wall -Wextra -Wpedantic
else
	C_WARNINGS =
endif

CFLAGS = $(C_WARNINGS) -std=$(C_STANDARD)
INCLUDE_FLAGS  = -I $(INCLUDE_DIR)
LDFLAGS =

ifeq ($(DEBUG), 1)
	CFLAGS += -g -O0
else
	CFLAGS += -O3
endif

C_COMPILER_CALL = $(CC) $(CFLAGS) $(INCLUDE_FLAGS)

C_SOURCES = $(wildcard $(SOURCE_DIR)/*.c)
C_OBJECTS = $(patsubst $(SOURCE_DIR)/%.c, $(BUILD_DIR)/%.o, $(C_SOURCES))

all: create build

create:
	@mkdir -p build

build: $(C_OBJECTS)
	$(C_COMPILER_CALL) $^ $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)

execute:
	@./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	@rm -rf $(BUILD_DIR)


$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.c
	$(C_COMPILER_CALL) -c $< -o $@


.PHONY: all create build execute clean
