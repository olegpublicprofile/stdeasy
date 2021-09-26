cmake_minimum_required(VERSION 3.8)
project(stdeasy LANGUAGES CXX)

####################################################################
# Library version
get_directory_property(hasParent PARENT_DIRECTORY)
if(NOT ${hasParent})

    add_library(${PROJECT_NAME} INTERFACE)
    target_include_directories(${PROJECT_NAME} INTERFACE "include/")

####################################################################
# Standalone version (for testing)
else()

    set(CMAKE_CXX_STANDARD 11)
    set(CMAKE_CXX_STANDARD_REQUIRED ON)

    file(GLOB_RECURSE SOURCES "tests/*.cpp")

    add_executable(${PROJECT_NAME} ${SOURCES})
    target_include_directories(${PROJECT_NAME} PUBLIC "include/" ".")

    set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE CXX)

    if(MSVC)
        target_compile_options(${PROJECT_NAME} PUBLIC
            /MP
            /FC
        )
    else()
        target_compile_options(${PROJECT_NAME} PUBLIC -Wall)
		if(CMAKE_COMPILER_IS_GNUCXX)
			target_link_libraries(${PROJECT_NAME} stdc++fs tbb)
		endif()
    endif()

endif()

