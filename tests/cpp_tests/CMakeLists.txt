project(Boost_Tests_run)

find_package (Boost REQUIRED COMPONENTS unit_test_framework)

add_executable (${PROJECT_NAME}
        basic_tests.cpp

        ${CMAKE_SOURCE_DIR}/src/Dataset.cpp
        ${CMAKE_SOURCE_DIR}/src/ParserTask.cpp
        ${CMAKE_SOURCE_DIR}/src/Chunk.cpp
        ${CMAKE_SOURCE_DIR}/src/FTDCParser.cpp
        ${CMAKE_SOURCE_DIR}/src/ParserTasksList.cpp
        ${CMAKE_SOURCE_DIR}/src/ConstDataRangeCursor.cpp
        ${CMAKE_SOURCE_DIR}/src/ChunkMetric.cpp
        ${CMAKE_SOURCE_DIR}/src/SampleLocation.cpp
        ${CMAKE_SOURCE_DIR}/src/include/SampleLocation.h
        ${CMAKE_SOURCE_DIR}/src/include/Timestamp.h
        ${CMAKE_SOURCE_DIR}/src/include/Metrics.h

        ${CMAKE_SOURCE_DIR}/src/WriterTaskList.cpp
        ${CMAKE_SOURCE_DIR}/src/include/WriterTaskList.h
        ${CMAKE_SOURCE_DIR}/src/WriterTask.cpp
        ${CMAKE_SOURCE_DIR}/src/include/WriterTask.h
        ${CMAKE_SOURCE_DIR}/src/JSONWriter.cpp
        ${CMAKE_SOURCE_DIR}/src/include/CSVWriter.h
        ${CMAKE_SOURCE_DIR}/src/CSVWriter.cpp
        ${CMAKE_SOURCE_DIR}/src/include/Timestamp.h
        )

target_include_directories (${PROJECT_NAME}  PUBLIC
        ${Boost_INCLUDE_DIRS}
        ${CMAKE_SOURCE_DIR}/src
        ${CMAKE_SOURCE_DIR}/src/include
        ${CMAKE_SOURCE_DIR}/src/mongo-c-driver/src/libbson/src
        ${CMAKE_CURRENT_BINARY_DIR}/../../src/mongo-c-driver/libbson
)

target_link_directories(${PROJECT_NAME} PUBLIC
        ${CMAKE_CURRENT_BINARY_DIR}/../../src/mongo-c-driver/src/libbson
)

target_link_libraries (${PROJECT_NAME}
        ${Boost_LIBRARIES}
        Boost::log
        bson-static-1.0.a
)

