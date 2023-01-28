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
CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic
CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = -lm

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O2
EXECUTABLE_NAME = mainRelease
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS)

CXX_SOURCES = $(wildcard *.cpp)
CXX_OBJECTS = $(patsubst %.cpp, %.o, $(CXX_SOURCES))

# target: prerequisites
# 		commands

build: clean sources $(CXX_OBJECTS)
	@echo "------------------------- Building ------------------------"
	$(COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)
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
	@./$(EXECUTABLE_NAME)

clean:
	@echo "-------------------------- Clean -------------------------"
	@rm -f $(EXECUTABLE_NAME) *.o
	@echo ""
	@echo "Done!"
	@echo "----------------------------------------------------------"

###############################################
# Patterns
# 
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the name of all prerequisites
%.o: %.cpp
	@echo "Generate object file $@"
	$(COMPILER_CALL) -c $< -o $@