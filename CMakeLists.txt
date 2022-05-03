cmake_minimum_required(VERSION 3.16.3)
project(bitsery
        LANGUAGES CXX
        VERSION 5.2.2)

find_package(ament_cmake REQUIRED)

add_library(${PROJECT_NAME} INTERFACE)

target_include_directories(${PROJECT_NAME} INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>)
target_compile_features(bitsery INTERFACE
  cxx_auto_type
  cxx_constexpr
  cxx_lambdas
  cxx_nullptr
  cxx_variadic_templates)

install(DIRECTORY include/ DESTINATION include/)
install(TARGETS ${PROJECT_NAME}
  EXPORT ${PROJECT_NAME}_Targets
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  INCLUDES DESTINATION include)

ament_export_include_directories(include)
ament_export_targets(${PROJECT_NAME}_Targets)

ament_package()
