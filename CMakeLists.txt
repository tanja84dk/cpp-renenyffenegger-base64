# CMakeLists.txt for Tools Collection
#
# © 2024 by Tanja84DK

cmake_minimum_required(VERSION 3.8)

project(renenyffenegger_base64 VERSION 2)

option(renenyffenegger_base64_BUILD_TESTING OFF)

option(BUILD_SHARED_LIBS OFF)

set(renenyffenegger_base64_HEADERS
	include/renenyffenegger/base64.h
)

set(renenyffenegger_base64_SOURCES
	src/base64.cpp
)


add_library(renenyffenegger_base64 ${renenyffenegger_base64_SOURCES})

add_library(ReneNyffenegger::base64 ALIAS renenyffenegger_base64)

target_include_directories(renenyffenegger_base64
	PUBLIC
		$<INSTALL_INTERFACE:include>
		$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
	PRIVATE
		${CMAKE_CURRENT_SOURCE_DIR}
)

target_compile_features(renenyffenegger_base64
	PRIVATE
		cxx_std_17
)

set_target_properties(renenyffenegger_base64
	PROPERTIES
		ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
    	LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
    	RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
		CXX_STANDARD 17
		VERSION ${renenyffenegger_base64_VERSION}
		SOVERSION ${renenyffenegger_base64_VERSION_MAJOR}
)

if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR OR renenyffenegger_base64_BUILD_TESTING STREQUAL ON)
	add_subdirectory(test)
endif()