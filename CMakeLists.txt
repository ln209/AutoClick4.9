cmake_minimum_required(VERSION 3.28)
project(AutoClick)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_DEFAULT 11)
file(GLOB_RECURSE SRC "include/*.h" "include/*.hpp" "src/*.cpp")



set(OpenCV_DIR "C:\\Users\\luisn\\Documents\\OpenCV\\build\\install") # ungefähr so: ".../build/install/"
#if (NOT "$ENV{OPEN_CV_PATH}" STREQUAL "")# nach dem Setzen der Umgebungsvariable neustarten
#    set(OpenCV_DIR "$ENV{OPEN_CV_PATH}" CACHE INTERNAL "Acquired opencv path from environmental variables")
#else ()
#    message(FATAL_ERROR "opencv has not been found, this build process requires opencv as an essential library. Please edit this CMakeLists.txt file or add the opencv folder to your environmental variables")
#endif ()

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

message(STATUS "OpenCV library status:")
message(STATUS "    config: ${OpenCV_DIR}")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")
add_executable(${PROJECT_NAME} ${SRC})

target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})