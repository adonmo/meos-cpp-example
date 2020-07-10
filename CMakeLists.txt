cmake_minimum_required(VERSION 3.14 FATAL_ERROR)
project(app VERSION 0.0.1)


# ---- Including MEOS (libmeos) as dependency using CPM ----
# For more info on CPM dependecies, see https://github.com/TheLartians/CPM.cmake

include(cmake/CPM.cmake)

CPMAddPackage(
  NAME libmeos
  GITHUB_REPOSITORY adonmo/meos
  # v0.0.8
  GIT_TAG c5fc6ffa8ce8760bd4fde0e588e40aac2eded592
)

# ---- Build example application ----

add_executable(app "${CMAKE_CURRENT_SOURCE_DIR}/source/main.cpp")
target_link_libraries(app libmeos)
