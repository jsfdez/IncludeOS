# Add drivers as libraries
#
# Note: we can't have all the drivers in the same library as we'll want
# e.g. several network drivers, which will result in conflicting symbols
#
# ...There are probably nicer solutions, so please PR if you know them.
add_library(virtioblk STATIC virtioblk.cpp)
add_dependencies(virtioblk PrecompiledLibraries)

add_library(virtionet STATIC virtionet.cpp)
add_dependencies(virtionet PrecompiledLibraries)

add_library(heap_debugging STATIC heap_debugging.cpp)
add_dependencies(heap_debugging PrecompiledLibraries)

add_library(silent_start STATIC silent.cpp)
add_dependencies(silent_start PrecompiledLibraries)


install(TARGETS virtionet virtioblk heap_debugging silent_start DESTINATION includeos/drivers)
