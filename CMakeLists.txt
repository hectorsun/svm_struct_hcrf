cmake_minimum_required(VERSION 2.8)
project( SvmSturct)
find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )


add_subdirectory(svm_light)
add_subdirectory(svm_struct)

add_library(svm_struct_api svm_struct_api.c )
add_library(svm_struct_learn_custom svm_struct_learn_custom.c )


add_executable(svm_hcrf_classify svm_struct/svm_struct_classify.c)
target_link_libraries(svm_hcrf_classify svm_common
                                        svm_struct_common
                                        svm_struct_api
                                        m ${OpenCV_LIBS})

add_executable(svm_hcrf_learn svm_struct/svm_struct_main.c)
target_link_libraries(svm_hcrf_learn svm_struct_learn
                                     svm_hideo svm_learn svm_common
                                     svm_struct_common
                                     svm_struct_api svm_struct_learn_custom
                                     m ${OpenCV_LIBS})
