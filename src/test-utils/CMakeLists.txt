project(test-utils)

# convert stl to c++ code to inclusion in test
add_executable(stl_to_cpp stl_to_cpp.cpp)

if (CMAKE_SYSTEM_NAME STREQUAL "Linux" OR CMAKE_SYSTEM_NAME STREQUAL "FreeBSD")
    include(FindX11)
    target_link_libraries(stl_to_cpp libslic3r X11::xcb)
else ()
    target_link_libraries(stl_to_cpp libslic3r)
endif ()

if (WIN32)
    prusaslicer_copy_dlls(stl_to_cpp)
endif()
