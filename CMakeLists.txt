cmake_minimum_required(VERSION 3.25.0)

set (CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -ffast-math")

project(Lspp
  LANGUAGES CXX
  VERSION 0.0.1
)

file(GLOB LSPP_SRC "src/*.cpp")

add_executable(ls++ ${LSPP_SRC})

install(TARGETS ls++ DESTINATION bin)

add_custom_target("uninstall" COMMENT "Uninstall installed files")
add_custom_command(
    TARGET "uninstall"
    POST_BUILD
    COMMENT "Uninstall files with install_manifest.txt"
    COMMAND xargs rm -vf < install_manifest.txt || echo Nothing in
            install_manifest.txt to be uninstalled!
)
