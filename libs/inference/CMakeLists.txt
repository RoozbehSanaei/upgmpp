# ----------------------------------------------------------------------------
# Master CMake file for the inference library of the UPGMpp project.
#
#  Started in February 2014, J.R. Ruiz-Sarmiento <jotaraul@uma.es>
#			University of Málaga
#			University of Osnabrück
#
#  NOTE: CMake can be obtained at http://www.cmake.org/
# ----------------------------------------------------------------------------

SET ( INFERENCE_LIB_NAME inference )
# TARGET:
FILE(GLOB aux_srcs1 ${CMAKE_SOURCE_DIR}/libs/${INFERENCE_LIB_NAME}/*.cpp)
FILE(GLOB aux_srcs2 ${CMAKE_SOURCE_DIR}/libs/${INFERENCE_LIB_NAME}/*.hpp)

SET(SRCS ${aux_srcs1} ${aux_srcs2})

ADD_LIBRARY(${INFERENCE_LIB_NAME} SHARED ${SRCS})

SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/libs)

TARGET_LINK_LIBRARIES(${INFERENCE_LIB_NAME} base)

install(TARGETS ${INFERENCE_LIB_NAME} DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES ${aux_srcs2} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/${PROJECT_NAME}/${INFERENCE_LIB_NAME}  )

