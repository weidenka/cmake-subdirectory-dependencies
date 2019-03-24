message(STATUS "CMake: A")
add_library(A SHARED A.hpp A.cpp)
target_include_directories(A PUBLIC "${CURRENT_SOURCE_DIR}")
install(TARGETS A EXPORT AA LIBRARY DESTINATION lib/)
export(TARGETS A NAMESPACE AA:: FILE ${CMAKE_BINARY_DIR}/A/AConfig.cmake)

add_library(AA::A ALIAS A)
file(WRITE ${CMAKE_BINARY_DIR}/A/AConfig.cmake "")
# include(CMakePackageConfigHelpers)
# write_basic_package_version_file(
#   ${CMAKE_BINARY_DIR}/A/AConfigVersion.cmake
#   VERSION 1.0.0
#   COMPATIBILITY AnyNewerVersion)
# set(A_DIR ${CMAKE_BINARY_DIR}/A CACHE PATH "")
# set(A_IMPORTED_TARGETS "AA::A")
