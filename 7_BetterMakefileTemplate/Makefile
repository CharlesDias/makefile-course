# Variables
# Note: Variables can only be strings
# Note: single or double quotes for variables names or values have no meaning to Makefile

# Predefined variables on Makefile. To see the predefined variable press "make -p" on terminal console
# Some examples of predefined variables on Makefile
#
# CC: Program for compiling C programs; default gcc
# CXX: Program for compiling C++ programs; default g++
# CFLAGS: Extra flags to give to the C complier
# CXXFLAGS: Extra flags to give to the C++ compiler
# CPPFLAGS: Extra flags to give to the C preprocessor
# LDFLAGS: Extra flags to give to the linker

DEBUG = 1
ENABLE__WARNINGS = 1
WARNINGS_AS_ERRORS = 0

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CXX_STANDARD = c++17
ifeq ($(ENABLE__WARNINGS), 1)
CXX_WARNINGS = -Wall -Wextra -Wpedantic
else
CXX_WARNINGS =
endif

ifeq ($(WARNINGS_AS_ERRORS), 1)
CXX_WARNINGS += -Werror
endif

CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)
LDFLAGS = -lm

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O2
EXECUTABLE_NAME = mainRelease
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cpp)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(CXX_SOURCES))

# target: prerequisites
# 		commands

create:
	mkdir -p build

build: create sources $(CXX_OBJECTS)
	@echo "------------------------- Building ------------------------"
	$(COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)
	@echo ""
	@echo "Done!"
	@echo "----------------------------------------------------------"

sources:
	@echo "---------------------- Sources files ---------------------"
	@echo $(CXX_SOURCES)
	@echo ""
	@echo "Done!"
	@echo "----------------------------------------------------------"

execute:
	@echo "------------------ Executing the program -----------------"
	@./$(BUILD_DIR)/$(EXECUTABLE_NAME)

clean:
	@echo "-------------------------- Clean -------------------------"
	rm -f $(BUILD_DIR)/*
	@echo ""
	@echo "Done!"
	@echo "----------------------------------------------------------"

###############################################
# Patterns
# 
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the name of all prerequisites
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	@echo "Generate object file $@"
	$(COMPILER_CALL) -c $< -o $@

###############################################
# Phony
# 
.PHONY: create build sources execute clean