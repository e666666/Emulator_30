.PHONY: all clean distclean
ROOT_DIR:=$(shell dirname $(realpath $(firstword $(MAKEFILE_LIST))))
GCC_DIR:=${ROOT_DIR}/../../../gcc-5

clang-r399163b/bin/clang:
	mkdir -p ../../../wd/clang-build
	cd ../../../wd/clang-build && \
	../../cmake/linux-x86/bin/cmake \
	-DCMAKE_INSTALL_PREFIX=${ROOT_DIR}/clang-r399163b \
	-G "Unix Makefiles" \
	-DCMAKE_BUILD_TYPE=Release \
	-DLLVM_ENABLE_PROJECTS="libcxx;libcxxabi;clang;clang-tools-extra;" \
	-DCMAKE_C_COMPILER="${GCC_DIR}/bin/gcc" \
	-DCMAKE_CXX_COMPILER="${GCC_DIR}/bin/g++" \
	-DCMAKE_CXX_LINK_FLAGS="-Wl,-rpath,${GCC_DIR}/lib64 -L${GCC_DIR}/toolchains/lib64" \
	../../tarballs/llvm-project/llvm && \
	make -j6 && \
	make install

clang-r399163b/lib64/libc++.so: clang-r399163b/bin/clang
	ln -sv lib clang-r399163b/lib64

clean:
	rm -rf clang-r399163b

distclean: clean
	rm -rf ../../../wd/clang-build

all: clang-r399163b/bin/clang clang-r399163b/lib64/libc++.so
