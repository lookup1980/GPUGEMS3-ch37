CPPFLAGS += -I -W -Wall -Wno-unused-parameter
LDLIBS += -lgsl -lgslcblas 

LDLIBS += -O3 -DNDEBUG
CUDA_LIBS += /usr/local/cuda-10.0/lib64
CUDA_INC += /usr/local/cuda-10.0/include
CUDA_INSTALL_PATH = /usr/local/cuda-10.0

CUDA_SDK_PATH = /usr/local/cuda-10.0/samples
CUDA_INSTALL_PATH = /usr/local/cuda-10.0
CUDA_SDK_LIBS = $(CUDA_SDK_PATH)/common/lib
CUDA_SDK_INCLUDE = $(CUDA_SDK_PATH)/common/inc


all: two_block_wallace
	g++ -o test test.cpp $(LDLIBS) $(CPPFLAGS) obj/cuda_rng_options.o -L$(CUDA_INSTALL_PATH)/lib -L$(CUDA_LIBS) -L$(CUDA_SDK_LIBS) -lcuda -lcudart -lGL -lGLU 

two_block_wallace:
	nvcc --compile -g cuda/cuda_rng_options.cu -D_DEBUG -o obj/cuda_rng_options.o -Xcompiler "-m32" -Xcompiler "" -I. -Icuda/ -I//usr/local/cuda-10.0/include -I$(CUDA_SDK_INCLUDE) -DUNIX -O3

clean:
	rm -f obj/*
	rm -f test
