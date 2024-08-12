add_executable(renenyffenegger_base64_test src/test.cpp)
target_link_libraries(renenyffenegger_base64_test PRIVATE ReneNyffenegger::base64)

include(CTest)
