cmake_minimum_required(VERSION 3.4.1)

include_directories(src/main/jni/include)
include_directories(src/main/jni)
aux_source_directory(src/main/jni SOURCE_FILES)
aux_source_directory(src/main/jni/src/core SOURCE_FILES_CORE)
aux_source_directory(src/main/jni/src/train SOURCE_FILES_TRAIN)
aux_source_directory(src/main/jni/src/util SOURCE_FILES_UTIL)
aux_source_directory(src/main/jni/thirdparty/LBP SOURCE_FILES_LBP)
aux_source_directory(src/main/jni/thirdparty/mser SOURCE_FILES_MSER)
aux_source_directory(src/main/jni/thirdparty/svm SOURCE_FILES_SVM)
aux_source_directory(src/main/jni/thirdparty/textDetect SOURCE_FILES_TEXTDETECT)
aux_source_directory(src/main/jni/thirdparty/xmlParser SOURCE_FILES_XML)
list(APPEND SOURCE_FILES ${SOURCE_FILES_CORE})
list(APPEND SOURCE_FILES ${SOURCE_FILES_SOURCE_FILES_SVM})
list(APPEND SOURCE_FILES ${SOURCE_FILES_CORE})
list(APPEND SOURCE_FILES ${SOURCE_FILES_TRAIN})
list(APPEND SOURCE_FILES ${SOURCE_FILES_UTIL})
list(APPEND SOURCE_FILES ${SOURCE_FILES_LBP})
list(APPEND SOURCE_FILES ${SOURCE_FILES_MSER})
list(APPEND SOURCE_FILES ${SOURCE_FILES_TEXTDETECT})
list(APPEND SOURCE_FILES ${SOURCE_FILES_XML})
set(OpenCV_DIR ${CMAKE_SOURCE_DIR}/OpenCV-android-sdk/sdk/native/jni)
find_package(OpenCV REQUIRED)

add_library( mrcar
             SHARED
             ${SOURCE_FILES})


find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )



target_link_libraries( # Specifies the target library.
                       mrcar
                       ${OpenCV_LIBS}
                       ${log-lib} )
