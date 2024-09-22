cmake_minimum_required(VERSION 3.22)
project(HELLOAPP)
set(SRC_FILES main.cpp src/calc.cpp)
message("SRC File has ${SRC_FILES}")
message("${CMAKE_SOURCE_DIR}")
if(EXISTS ${CMAKE_SOURCE_DIR}/main.cpp)
    message("all is good")
else()
    message( FATAL_ERROR "file not exist")
endif()
set(VAR 10)
while(VAR)
    message(${VAR})
    math(EXPR VAR "${VAR} - 1")
endwhile(VAR)
#Options:
# OpVar will be writen as a comment over on the cash file
option(OpVar "BOOL Var" true) 
# another way to save a specific value in cash 
# set(VAR TRUE CACHE BOOL "bool variable")

add_subdirectory(${CMAKE_SOURCE_DIR}/include)
add_subdirectory(${CMAKE_SOURCE_DIR}/lib)
add_executable(HELLOAPP ${SRC_FILES})
target_include_directories(HELLOAPP PUBLIC include/ lib/)
target_link_libraries(HELLOAPP PUBLIC wifi_lib)

#Add comment dummy just to triger jenkins
#trying web hook

