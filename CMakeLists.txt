cmake_minimum_required(VERSION "3.7.1")

project("HelloWorld")   #Create the name of the project

# Create the executable name using first arg
    # Using the 2nd args as the source file
add_executable("${PROJECT_NAME}" "Main.cpp")

# Install will put the targets to destination
    # bin is relative path to CMAKE_INSTALL_PREFIX/bin
install(TARGETS "${PROJECT_NAME}" DESTINATION bin)

# install Main.cpp file
install(FILES "Main.cpp" DESTINATION src)   #So in folder "C:/Program Files/${PROJECT_NAME}/src"

# USE cmake --install for the program to install into C:/Program Files (x86)

## EP 2
# Using CTest - Test your code, automatically include a bunch of tool to test your code
include(CTest)

# add_test 1st arg = name of the test
        # 2nd arg = The build/ folder
# After finishing cmake and build, go into build folder
# and run "ctest"

# CMAKE_CURRENT_BINARY_DIR = build/ directory
# Use PROJECT_NAME because that's the executable we created

# test passed if the return is 0, false if anything else
add_test("test1" "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}")
# We added another parameter for our .exe in our second test -> gona return 1 -> fail test2
add_test("test2" "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}" "someparameter")