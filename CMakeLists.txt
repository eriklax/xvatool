CMAKE_MINIMUM_REQUIRED(VERSION 3.0)

LINK_DIRECTORIES(/usr/local/lib)
INCLUDE_DIRECTORIES(SYSTEM
	/usr/local/include
)

SET(CMAKE_CXX_FLAGS_RELEASE "-Wall -Wextra -Wvla")
SET(CMAKE_BUILD_TYPE Release)

PROJECT("xva-img")
FIND_PACKAGE(OpenSSL REQUIRED)
SET(TARGET_NAME "xva-img")
FILE(GLOB_RECURSE SOURCE_FILES src/*.cpp)
ADD_EXECUTABLE(${TARGET_NAME} ${SOURCE_FILES})
TARGET_LINK_LIBRARIES(${TARGET_NAME}
	crypto
	xxhash
)
INSTALL(PROGRAMS ${CMAKE_CURRENT_BINARY_DIR}/xva-img
	DESTINATION bin)
