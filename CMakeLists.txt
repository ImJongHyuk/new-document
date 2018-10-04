cmake_minimum_required(VERSION 3.3)
project(new-document)

################ Developer Setting Zone ################
# TARGET setting #
set( BUILD_TARGET exe )
set( BUILD_TYPE   Debug )
# Set Executable & Library name #
set( EXECUTABLE_NAME "newdocu" )
set( LIBRARY_NAME "newdocu" )
########################################################

set( SRC_ROOT_PATH "./src" )

AUX_SOURCE_DIRECTORY( ${SRC_ROOT_PATH}  SRC_ROOT_DIR_SOURCES )

set( SOURCE_FILES
        ${SRC_ROOT_DIR_SOURCES})

# Header files
set( HEADER_FILES )


################### GCC Setting Zone ###################
set( CMAKE_CXX_STANDARD 11 )
set( CMAKE_BUILD_TYPE ${BUILD_TYPE} )
message( STATUS "Cmake Build Type: ${CMAKE_BUILD_TYPE}" )

if ( CMAKE_BUILD_TYPE MATCHES Release )
    set(CMAKE_CONFIGURATION_TYPES Release)
    set(CMAKE_CXX_FLAGS_RELEASE "-O2")
endif()
if ( CMAKE_BUILD_TYPE MATCHES Debug )
    set(CMAKE_CXX_FLAGS_DEBUG "-g")
endif()
########################################################


#####################   BUILD Zone  ####################
if ( BUILD_TARGET MATCHES exe )
    set( TARGET_NAME ${EXECUTABLE_NAME} )
    # Add Executable
    add_executable( ${TARGET_NAME} ${SOURCE_FILES} ${HEADER_FILES})
endif()

if ( BUILD_TARGET MATCHES lib )
    set( TARGET_NAME ${LIBRARY_NAME} )
    # Add Library
    add_library( ${TARGET_NAME} ${SOURCE_FILES} ${HEADER_FILES})
endif()

# target_link_libraries(${TARGET_NAME})
########################################################