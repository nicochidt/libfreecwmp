cmake_minimum_required(VERSION 2.6)
PROJECT(libfreecwmp)
ADD_DEFINITIONS(-Wall -Werror --std=gnu99 -Wmissing-declarations)

INCLUDE_DIRECTORIES(${LIBFREECWMP_SOURCE_DIR})
FILE(MAKE_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib)

SET(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib)
SET(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/lib)
SET(SOURCES
	src/libfreecwmp.c
	src/libfreecwmp.h
)

ADD_LIBRARY(libfreecwmp_shared SHARED ${SOURCES})
ADD_LIBRARY(libfreecwmp_static STATIC ${SOURCES})

SET_TARGET_PROPERTIES(libfreecwmp_shared PROPERTIES OUTPUT_NAME freecwmp)
SET_TARGET_PROPERTIES(libfreecwmp_static PROPERTIES OUTPUT_NAME freecwmp)

INSTALL(TARGETS libfreecwmp_shared LIBRARY DESTINATION lib)
INSTALL(TARGETS libfreecwmp_static ARCHIVE DESTINATION lib)
INSTALL(FILES src/libfreecwmp.h DESTINATION include)
