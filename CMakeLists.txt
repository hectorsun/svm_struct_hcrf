cmake_minimum_required(VERSION 2.8)
project( SvmSturct)
find_package( OpenCV REQUIRED )
find_package(Boost REQUIRED COMPONENTS serialization)

include_directories( ${OpenCV_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})

add_subdirectory(svm_light)


add_executable(svm_hcrf_classify svm_struct_api.cpp svm_struct/svm_struct_classify.cpp svm_struct/svm_struct_common.cpp)
target_link_libraries(svm_hcrf_classify svm m ${OpenCV_LIBS} ${Boost_LIBRARIES})

add_executable(svm_hcrf_learn svm_struct_api.cpp svm_struct_learn_custom.cpp  svm_struct/svm_struct_main.cpp svm_struct/svm_struct_learn.cpp svm_struct/svm_struct_common.cpp)
target_link_libraries(svm_hcrf_learn svm  m ${OpenCV_LIBS} ${Boost_LIBRARIES})
