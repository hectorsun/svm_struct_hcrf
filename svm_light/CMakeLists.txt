message("svm_light")

#add_library(svm_hideo svm_hideo.c)
#add_library(svm_common svm_common.c)
#add_library(svm_learn svm_learn.c)
#add_library(svm_learn_main svm_learn_main.c)
#add_library(svm_classify svm_classify.c)

add_library(svm SHARED  svm_hideo.c svm_common.c svm_learn.c )
