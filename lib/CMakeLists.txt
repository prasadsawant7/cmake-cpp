add_library(mylib lib.cpp)

# Includes header files
# Similar to Private, Public, Protected in cpp
# PRIVATE | PUBLIC | INTERFACE (For Real Library use INTERFACE)
# Header file accessed as a interface to use this library
target_include_directories(mylib
	INTERFACE
	${CMAKE_CURRENT_SOURCE_DIR})

# Three keyword in target_include_directories
# PRIVATE => It's used for the current target which in this case is mylib as mentioned in target_include_directories() but it's not used by dependencies of mylib or other parts of the program that uses mylib.
# PUBLIC => It means it's used by both mylib and the dependencies.
# INTERFACE => It means it's used by only dependencies and isn't needed for mylib.

# In this case INTERFACE is the right choice
# Because mylib knows where to find lib.h its in the current directory of the source files so it doesn't need to know where to find those.
# But other dependencies that would use mylib they need to know where to find those header files so we wanna make this INTERFACE.
