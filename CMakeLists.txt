cmake_minimum_required(VERSION 3.20)
set(PATCH_VERSION "1" CACHE INTERNAL "Patch version")
set(PROJECT_VESRION 0.0.${PATCH_VERSION})

project(helloworld VERSION ${PROJECT_VESRION})
set(CMAKE_CXX_STANDARD 17)

set(EXEC_NAME ${PROJECT_NAME}_cli)

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/version.h.in" "${CMAKE_CURRENT_SOURCE_DIR}/version.h")

add_executable(${EXEC_NAME} main.cpp lib.cpp)

target_compile_options(${EXEC_NAME} PRIVATE -Wall -Wextra -pedantic -Werror)

set(CPACK_PACKAGE_CONTACT mugutdinov@yandex.ru)
set(CPACK_GENERATOR DEB)
install(TARGETS ${EXEC_NAME} RUNTIME DESTINATION bin)
include(CPack)