# SPDX-License-Identifier: Apache-2.0
if (CONFIG_RCLC)

zephyr_library_named(rclc)

target_compile_definitions(rclc PUBLIC
  ROS_PACKAGE_NAME=rolling
  )

target_compile_options(rclc PRIVATE -Wno-unused-variable -Wno-implicit-function-declaration -Wno-int-conversion)

zephyr_include_directories(
  ${ZEPHYR_CURRENT_MODULE_DIR}/rclc/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/../rosidl_runtime_c/include
  ${CMAKE_BINARY_DIR}/modules/rcl_interaces/include
  )

zephyr_library_include_directories(
  ${ZEPHYR_CURRENT_MODULE_DIR}/rclc/include
  ${ZEPHYR_CURRENT_MODULE_DIR}/../rosidl_runtime_c/include
  ${CMAKE_BINARY_DIR}/modules/rcl_interaces/include
  )

file(GLOB_RECURSE Sources
  "${ZEPHYR_CURRENT_MODULE_DIR}/rclc/src/*.c"
)

#message(STATUS "Sources: ${Sources}")

zephyr_library_sources(
  ${Sources}
)

endif()
