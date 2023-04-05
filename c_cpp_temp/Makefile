APP_NAME := main
CC := gcc
DEBUG := 1
COMPILE_FLAGS_RELEACE := -O3
COMPILE_FLAGS_DEBUG := -O0 -g -Wall -Wextra
SOURCE_DIRS := $(shell find . -type d)


ifeq ($(DEBUG), 1)

$(shell mkdir -p build)
$(shell mkdir -p build/debug)
$(shell mkdir -p build/debug/app)
$(shell mkdir -p build/debug/objects)

COMPILE_FLAGS := $(COMPILE_FLAGS_DEBUG)
BUILD_DIR := debug

else

$(shell mkdir -p build)
$(shell mkdir -p build/release)
$(shell mkdir -p build/release/app)
$(shell mkdir -p build/release/objects)
COMPILE_FLAGS := $(COMPILE_FLAGS_RELEACE)
BUILD_DIR := release

endif


SOURCES := $(addsuffix /*.c, $(SOURCE_DIRS))
SOURCES := $(notdir $(patsubst %.c, %.o, $(wildcard $(SOURCES))))
BUILD_SOURCES := $(addprefix build/$(BUILD_DIR)/objects/, $(SOURCES))
INCLUDE_DIRS := $(addprefix -I , $(SOURCE_DIRS))


VPATH := $(SOURCE_DIRS)


$(APP_NAME): $(SOURCES)
	$(CC) $(BUILD_SOURCES) -o build/$(BUILD_DIR)/app/$@

%.o: %.c
	$(CC) -c -MMD $(INCLUDE_DIRS) $(COMPILE_FLAGS) $< -o build/$(BUILD_DIR)/objects/$@

include $(wildcard build/$(BUILD_DIR)/objects/*.d)


clean:
	@rm -rf build

clean_debug:
	@rm -rf build/debug

clean_release:
	@rm -rf build/release

d:
	@./build/debug/app/$(APP_NAME)

r:
	@./build/release/app/$(APP_NAME)

.PHONY: clean clean_debug clean_release d r

