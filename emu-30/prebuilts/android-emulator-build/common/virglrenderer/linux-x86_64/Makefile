.PHONY: all clean distclean
ROOT_DIR:=$(shell dirname $(realpath $(firstword $(MAKEFILE_LIST))))

lib/libvirglrenderer.a:
	mkdir -p ../../../../wd/virgl-build
	cd ../../../../wd/virgl-build && \
	PKG_CONFIG_PATH="/home/builder/wd/prebuilts/libepoxy/lib/pkgconfig:/home/builder/wd/prebuilts/libgbm" ../../tarballs/virglrenderer/configure --disable-shared --enable-static --prefix=$(ROOT_DIR) --enable-autotools && \
	make -j6 && \
	make install

clean:
	rm -rf bin/ include/ lib/

distclean: clean
	rm -rf ../../../../wd/virgl-build

all: lib/libvirglrenderer.a
