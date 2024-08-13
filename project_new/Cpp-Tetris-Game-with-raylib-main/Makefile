.PHONY: all clean

PROJECT_NAME       ?= game
RAYLIB_VERSION     ?= 4.5.0
RAYLIB_PATH        ?= ..\..\raylib

COMPILER_PATH      ?= C:/raylib/w64devkit/bin
export PATH := $(COMPILER_PATH);$(PATH)

PLATFORM           ?= PLATFORM_DESKTOP
PLATFORM_OS        = WINDOWS

BUILD_MODE         ?= RELEASE
CFLAGS             = -Wall -std=c++14 -D_DEFAULT_SOURCE
ifeq ($(BUILD_MODE),DEBUG)
    CFLAGS += -g -O0
else
    CFLAGS += -s -O1
endif

CC                 = g++
MAKE               = mingw32-make

INCLUDE_PATHS      = -I. -I$(RAYLIB_PATH)/src -I$(RAYLIB_PATH)/src/external
LDFLAGS            = -L$(RAYLIB_PATH)/src -mconsole
LDLIBS             = -lraylib -lopengl32 -lgdi32 -lwinmm

SRC_DIR            = src
OBJ_DIR            = obj

SRC                = $(wildcard $(SRC_DIR)/*.c)
OBJS               = $(SRC:$(SRC_DIR)/%.c=$(OBJ_DIR)/%.o)

all: $(PROJECT_NAME)


$(PROJECT_NAME): $(OBJS)
	$(CC) -o $(PROJECT_NAME) $(OBJS) $(CFLAGS) $(INCLUDE_PATHS) $(LDFLAGS) $(LDLIBS)


$(OBJ_DIR)/%.o: $(SRC_DIR)/%.c
	$(CC) -c $< -o $@ $(CFLAGS) $(INCLUDE_PATHS)


clean:
	del /q $(OBJ_DIR)\*.o $(PROJECT_NAME).exe
	@echo Cleaning done
