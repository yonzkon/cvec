include_directories(../src)

add_executable(test-vec test-vec.c)
target_link_libraries(test-vec cmocka srrp)
add_test(test-vec ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/test-vec)
