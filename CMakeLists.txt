cmake_minimum_required(VERSION 3.5)

project(casadi_vendor)

find_package(ament_cmake REQUIRED)

include(ExternalProject)
ExternalProject_Add(casadi
  GIT_REPOSITORY  https://github.com/casadi/casadi.git
  GIT_TAG         3.5.5
  CMAKE_ARGS
    -DCMAKE_INSTALL_PREFIX=${CMAKE_CURRENT_BINARY_DIR}/casadi_install
    -DWITH_IPOPT=ON
)

install(
  DIRECTORY   ${CMAKE_CURRENT_BINARY_DIR}/casadi_install/
  DESTINATION ${CMAKE_INSTALL_PREFIX}
)

ament_export_include_directories(include)
ament_export_libraries(casadi)
ament_package()
