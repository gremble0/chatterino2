project(chatterino-benchmark)

set(benchmark_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/src/main.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/Emojis.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/Highlights.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/FormatTime.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/Helpers.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/LimitedQueue.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/LinkParser.cpp
    # Add your new file above this line!
    )

add_executable(${PROJECT_NAME} ${benchmark_SOURCES})
add_sanitizers(${PROJECT_NAME})

target_link_libraries(${PROJECT_NAME} PRIVATE chatterino-lib)
target_link_libraries(${PROJECT_NAME} PRIVATE chatterino-mocks)

target_link_libraries(${PROJECT_NAME} PRIVATE benchmark::benchmark)

set_target_properties(${PROJECT_NAME}
    PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
    RUNTIME_OUTPUT_DIRECTORY_RELEASE "${CMAKE_BINARY_DIR}/bin"
    RUNTIME_OUTPUT_DIRECTORY_DEBUG "${CMAKE_BINARY_DIR}/bin"
    RUNTIME_OUTPUT_DIRECTORY_RELWITHDEBINFO "${CMAKE_BINARY_DIR}/bin"
    )
