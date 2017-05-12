# fairSeq tbc troble.

* https://github.com/facebookresearch/fairseq


* Install command is `luarocks make rocks/fairseq-scm-1.rockspec`


## Trouble.
* In my case, I meet tbc error when I execute `luarocks make rocks/fairseq-scm-1.rockspec`
* error message is `nvcc fatal   : redefinition of argument 'std'`

## Shootting

* download tbc : `git clone git://github.com/gchanan/TemporalConvolutionTBC.git`
* make

```
cmake -E make_directory build && cd build && cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_PREFIX_PATH="/home/user/torch/install/bin/.." -DCMAKE_INSTALL_PREFIX="/home/user/torch/install/lib/luarocks/rocks/tbc/scm-1" && make
-- Found Torch7 in /home/user/torch/install
-- CUDA Found
-- Autodetected CUDA architecture(s): 6.1 6.1 6.1 6.1 6.1 6.1 6.1 6.1
-- Configuring done
-- Generating done
-- Build files have been written to: /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/build
[ 50%] Building NVCC (Device) object lib/CMakeFi/home/user/les/THTBC.dir//./THTBC_generated_init_cuda.cu.o
-- Removing /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/build/lib/CMakeFiles/THTBC.dir//./THTBC_generated_init_cuda.cu.o
/usr/bin/cmake -E remove /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/build/lib/CMakeFiles/THTBC.dir//./THTBC_generated_init_cuda.cu.o
-- Generating dependency file: /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/build/lib/CMakeFiles/THTBC.dir//THTBC_generated_init_cuda.cu.o.NVCC-depend
/usr/local/cuda/bin/nvcc -M -D__CUDACC__ /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/lib/init_cuda.cu -o /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/build/lib/CMakeFiles/THTBC.dir//THTBC_generated_init_cuda.cu.o.NVCC-depend -ccbin /usr/bin/cc -m64 --std c++11 -DTORCH_TBC_CUDA -DTHTBC_EXPORTS -Xcompiler ,\"-fPIC\",\"-O3\",\"-DNDEBUG\" -std c++11 -DNVCC -I/home/user/dev/fairseq/tmp/TemporalConvolutionTBC/lib -I/usr/local/cuda/include -I/home/user/torch/install/include -I/home/user/torch/install/include/TH -I/usr/local/cuda/include -I/home/user/torch/install/include/THC
nvcc fatal   : redefinition of argument 'std'
CMake Error at THTBC_generated_init_cuda.cu.o.cmake:207 (message):
  Error generating
  /home/user/dev/fairseq/tmp/TemporalConvolutionTBC/build/lib/CMakeFiles/THTBC.dir//./THTBC_generated_init_cuda.cu.o


make[2]: *** [lib/CMakeFiles/THTBC.dir/./THTBC_generated_init_cuda.cu.o] Error 1
make[1]: *** [lib/CMakeFiles/THTBC.dir/all] Error 2
make: *** [all] Error 2
```

* `vi ./lib/CMakeFiles/THTBC.dir/THTBC_generated_init_cuda.cu.o.cmake`
* change

```
# before
set(nvcc_flags -m64;--std;c++11;-DTORCH_TBC_CUDA;-DTHTBC_EXPORTS) # list
# after
set(nvcc_flags -m64;-DTORCH_TBC_CUDA;-DTHTBC_EXPORTS) # list
```
* then `make install`

