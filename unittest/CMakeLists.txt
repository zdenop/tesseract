# GTest include code would
# go somewhere in here

include(GoogleTest)

# F:\Projects\Community\tesseract\src\ccutil\errcode.h
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src/ccutil )
# C:\Users\zdenko.podobny\Projects\Community\tesseract\src\ccstruct\ocrblock.h
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src/ccstruct )
# C:\Users\zdenko.podobny\Projects\Community\tesseract\src\viewer\scrollview.h
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src/viewer )
# F:\Projects\Community\tesseract.zdenop\include\tesseract\export.h
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../include )
# "F:\Projects\Personal\mininalistic\tesseract\src\training\fileio.h"
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src/training/unicharset )
# F:\Projects\Community\tesseract\build.msvc.Release\src\training\unicharset_training_export.h
include_directories(${CMAKE_CURRENT_BINARY_DIR}/src/training )

add_definitions("-DTESTING_DIR=\"${CMAKE_CURRENT_SOURCE_DIR}/../test/testing\"")
add_definitions("-DTESSDATA_DIR=\"${CMAKE_CURRENT_SOURCE_DIR}/../tessdata\"")

add_executable(apiexample_test apiexample_test.cc)
target_link_libraries(
  apiexample_test
  PUBLIC unicharset_training
  libtesseract
  common_training
  GTest::gtest_main
)

add_executable(baseapi_test baseapi_test.cc)
target_link_libraries(
  baseapi_test
  PUBLIC unicharset_training
  libtesseract
  common_training
  GTest::gtest_main
)

add_executable(apiexample_test apiexample_test.cc)
target_link_libraries(
  apiexample_test
  PUBLIC unicharset_training
  libtesseract
  common_training
  GTest::gtest_main
)

add_executable(baseapi_thread_test baseapi_thread_test.cc)
target_link_libraries(
  baseapi_thread_test
  PUBLIC unicharset_training
  libtesseract
  common_training
  GTest::gtest_main
)

gtest_discover_tests(apiexample_test baseapi_test baseapi_thread_test)


# add_test(baseapi_gtests baseapi_test.cc)