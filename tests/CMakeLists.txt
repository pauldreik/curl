

# If fuzzing is enabled, include it from the curl-fuzzer repo
# so the curl repo does not need more fuzzer boilerplate than
# necessary. This assumes the curl-fuzzer repo is available
# parallel to curl.
# The reason for not building the unit tests is to speed up
# the build, while still having the macros enabled by testing
# turned on to make sure the fuzzing works.
if(ENABLE_FUZZING)
    include(${CMAKE_SOURCE_DIR}/../curl-fuzzer/intree_fuzzer/CMakeLists.txt)
else()
    add_subdirectory(data)
    add_subdirectory(libtest)
    add_subdirectory(server)
    add_subdirectory(unit)
endif()

