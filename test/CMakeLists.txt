enable_testing()
include(FetchGoogleTest)
include(GoogleTest)
add_executable(snowboy-test
    helper.cpp
    inspector.cpp
    ClassifyTest.cpp
    EnrollTest.cpp
    DtwTest.cpp
    CutTest.cpp
    VectorTest.cpp
)
target_include_directories(snowboy-test PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(snowboy-test snowboy gtest gtest_main crypto)
gtest_discover_tests(snowboy-test)

if(LTOAvailable)
    set_property(TARGET snowboy-test PROPERTY INTERPROCEDURAL_OPTIMIZATION TRUE)
endif()