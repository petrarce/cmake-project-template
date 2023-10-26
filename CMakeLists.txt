project( CppTemplate LANGUAGES C CXX )
cmake_minimum_required( VERSION 3.16 )
include(default.cmake)


find_package( Qt${QT_MAJOR_VERSION} COMPONENTS Core )
find_package( absl )
find_package( benchmark )

# Put your sources for the executable here
add_executable(main main.cpp)

if(benchmark_FOUND)
	target_link_libraries( main PRIVATE benchmark::benchmark )
endif()

if( TARGET Qt${QT_MAJOR_VERSION}::Core )
	target_link_libraries( main PRIVATE Qt${QT_MAJOR_VERSION}::Core )
endif()
