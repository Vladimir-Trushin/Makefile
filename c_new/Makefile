APP_NAME := main
SOURCE_DIRS := . editor text_line
CC := gcc
DEBUG := 1


ifeq ($(DEBUG), 1)

$(shell mkdir -p debug)
COMPILE_FLAGS := -O0 -g -Wall -Wextra
BUILD_DIR := debug

else

$(shell mkdir -p release)
COMPILE_FLAGS := -O3
BUILD_DIR := release

endif


SOURCES := $(addsuffix /*.c, $(SOURCE_DIRS))
SOURCES := $(notdir $(patsubst %.c, %.o, $(wildcard $(SOURCES))))
BUILD_SOURCES := $(addprefix $(BUILD_DIR)/, $(SOURCES))
INCLUDE_DIRS := $(addprefix -I , $(SOURCE_DIRS))


VPATH := $(SOURCE_DIRS)


$(APP_NAME): $(SOURCES)
	$(CC) $(BUILD_SOURCES) -o ./$(BUILD_DIR)/$@

%.o: %.c
	$(CC) -c -MD $(INCLUDE_DIRS) $(COMPILE_FLAGS) $< -o ./$(BUILD_DIR)/$@

include $(wildcard *.d)


clean:
	@rm -rf debug
	@rm -rf release

exe:
	@./$(BUILD_DIR)/$(APP_NAME)

.PHONY: clean exe

