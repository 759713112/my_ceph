add_library(ceph_example SHARED compressor_plugin_example.cc)
target_link_libraries(ceph_example ceph-common)

# unittest_compression
add_executable(unittest_compression
  test_compression.cc
  $<TARGET_OBJECTS:unit-main>
  )
add_ceph_unittest(unittest_compression)
target_link_libraries(unittest_compression global GTest::GTest)
add_dependencies(unittest_compression ceph_example)