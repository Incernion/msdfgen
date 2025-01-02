cmake_minimum_required(VERSION 3.16)

project(msdfgen LANGUAGES C CXX)

add_subdirectory(freetype)

# Add msdfgen static library
add_library(msdfgen STATIC)
set_target_properties(msdfgen PROPERTIES CXX_STANDARD 17)

# MSDFGen sources
file(GLOB_RECURSE MSDFGEN_SOURCES
        core/**.h
        core/**.hpp
        core/**.cpp
        ext/**.h
        ext/**.hpp
        ext/**.cpp
        lib/**.cpp
        include/**.h
)

target_sources(msdfgen PUBLIC ${MSDFGEN_SOURCES})
target_include_directories(msdfgen PUBLIC include freetype/include)
target_compile_definitions(msdfgen PRIVATE MSDFGEN_USE_CPP11)
target_link_libraries(msdfgen PRIVATE freetype)



