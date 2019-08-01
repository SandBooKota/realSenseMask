cmake_minimum_required(VERSION 3.1.0)

project(trackingSCARA)

find_package(OpenCV REQUIRED)
set(DEPENDENCIES realsense2 ${OpenCV_LIBS})

add_executable(rs-hsvmask rs-hsvmask.cpp cv-helpers.hpp)
set_property(TARGET rs-hsvmask PROPERTY CXX_STANDARD 11)
target_link_libraries(rs-hsvmask m ${DEPENDENCIES})

set_target_properties (rs-hsvmask PROPERTIES
	FOLDER "Examples/OpenCV"
)

install(
	TARGETS

	rs-hsvmask

	RUNTIME DESTINATION
	${CMAKE_INSTALL_PREFIX}/bin
)
