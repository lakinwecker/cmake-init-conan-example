cmake_minimum_required(VERSION 3.14)

include(cmake/prelude.cmake)

project(
    conan-example
    VERSION 0.1.0
    DESCRIPTION "Short description"
    HOMEPAGE_URL "https://example.com/"
    LANGUAGES CXX
)

include(cmake/project-is-top-level.cmake)
include(cmake/variables.cmake)

find_package(imgui REQUIRED)
find_package(Eigen3 REQUIRED)

# ---- Declare executable ----

add_executable(conan-example_exe source/main.cpp)
add_executable(conan-example::exe ALIAS conan-example_exe)

set_target_properties(
    conan-example_exe PROPERTIES
    OUTPUT_NAME conan-example
    EXPORT_NAME exe
)

target_compile_features(conan-example_exe PRIVATE cxx_std_17)

target_link_libraries(conan-example_exe PRIVATE imgui::imgui Eigen3::Eigen)

# ---- Install rules ----

if(NOT CMAKE_SKIP_INSTALL_RULES)
  include(cmake/install-rules.cmake)
endif()

# ---- Developer mode ----

if(NOT conan-example_DEVELOPER_MODE)
  return()
elseif(NOT PROJECT_IS_TOP_LEVEL)
  message(
      AUTHOR_WARNING
      "Developer mode is intended for developers of conan-example"
  )
endif()

include(CTest)
if(BUILD_TESTING)
  add_subdirectory(test)
endif()
