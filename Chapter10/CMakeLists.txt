# cmake for OpenCV Cookbook 3rd edition chapter 10
# your opencv/build directory should be in your system PATH

# set minimum required version for cmake
cmake_minimum_required(VERSION 3.16)
option(BUILD_ESTIMATE_F      "Build estimateF "      OFF)
option(BUILD_ROBUSTMATCHING  "Build robustmatching " ON)
option(BUILD_ESTIMATE_H      "Build estimateH "      OFF)
option(BUILD_MATCHING_TARGET "Build matchingTarget " OFF)

if(BUILD_ESTIMATE_F)
    add_executable( estimateF estimateF.cpp)
    target_link_libraries( estimateF ${OpenCV_LIBS})
endif()
if(BUILD_ROBUSTMATCHING)
    add_executable( robustmatching robustmatching.cpp)
    target_link_libraries( robustmatching ${OpenCV_LIBS})
endif()
if(BUILD_ESTIMATE_H)
    add_executable( estimateH estimateH.cpp)
    target_link_libraries( estimateH ${OpenCV_LIBS})
endif()
if(BUILD_MATCHING_TARGET)
    add_executable( matchingTarget matchingTarget.cpp)
    target_link_libraries( matchingTarget ${OpenCV_LIBS})
endif()


# copy required images to every directory with executable
SET (IMAGES ${CMAKE_SOURCE_DIR}/images/church01.jpg 
            ${CMAKE_SOURCE_DIR}/images/church02.jpg
            ${CMAKE_SOURCE_DIR}/images/church03.jpg
            ${CMAKE_SOURCE_DIR}/images/parliament1.jpg
            ${CMAKE_SOURCE_DIR}/images/parliament2.jpg
            ${CMAKE_SOURCE_DIR}/images/parliament3.jpg
            ${CMAKE_SOURCE_DIR}/images/cookbook1.bmp
            ${CMAKE_SOURCE_DIR}/images/objects.jpg)
FILE(COPY ${IMAGES} DESTINATION .)
FILE(COPY ${IMAGES} DESTINATION "Debug")
FILE(COPY ${IMAGES} DESTINATION "Release")