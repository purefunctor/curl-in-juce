project(VendorCode)

add_library(VendorCode STATIC include/vendor.hpp src/vendor.cpp)
target_include_directories(VendorCode
    PUBLIC 
        $<INSTALL_INTERFACE:include> 
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

set(HTTPLIB_COMPILE ON)
set(HTTPLIB_INSTALL OFF)

add_subdirectory(cpp-httplib)
target_link_libraries(VendorCode httplib)
