set(PYTHON_FILES
    openpose.py
    __init__.py
    _openpose.cpp)

add_library(_openpose SHARED ${PYTHON_FILES})
target_link_libraries(_openpose openpose ${GLOG_LIBRARY} ${GFLAGS_LIBRARY} ${Caffe_LIBS} ${MKL_LIBS} ${GLUT_LIBRARY} ${SPINNAKER_LIB} ${OpenCL_LIBRARIES} ${CMAKE_THREAD_LIBS_INIT})
SET_TARGET_PROPERTIES(_openpose PROPERTIES PREFIX "")
configure_file(openpose.py openpose.py)
configure_file(__init__.py __init__.py)

#install(TARGETS _openpose DESTINATION python)
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/ DESTINATION python/openpose FILES_MATCHING PATTERN "*.so")
install(DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/ DESTINATION python/openpose FILES_MATCHING PATTERN "*.py")
