cmake_minimum_required(VERSION 3.8)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/KotlinCMakeModule)

project(HelloTensorflow Kotlin)

cinterop(
        NAME tensorflow_kt
        DEF_FILE src/c_interop/tensorflow.def
        COMPILER_OPTS "-I/Users/sergey/.konan/third-party/tensorflow/include"
)

konanc_executable(
        NAME HelloTensorflow
        SOURCES src/kotlin/
        LIBRARIES tensorflow_kt
        LINKER_OPTS "-L/Users/sergey/.konan/third-party/tensorflow/lib -ltensorflow"
)