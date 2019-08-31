# mediastation-server

## Compiling external libs

### zlib
```
make
```
Lib can be found in `./libz.a`.


### curl
```
export MACOSX_DEPLOYMENT_TARGET="10.14"
./configure --disable-shared --enable-static
make
```
Lib can be found in `./lib/.libs/libcurl.a`.

### jpeglib (9c)
```
./configure --disable-shared --enable-static
make
```
Lib can be found in `./.libs/libjpeg.a`.

### libpng
```
cp scripts/makefile.XXXX Makefile
make libpng.a
```
Lib can be found in `./.libs/libpng16.a`.

### libtiff
Does not compile on MacOS

### ptypes
```
make
```
Lib can be found in `./lib/libtypes.a`.

### tinyxml
```
make
```

### taglib
```
cmake .
make
```

### boost
```
./configure
make
```

### miniupnpc
```
make
```
Lib can be found in `./libminiupnpc.a`

### jsoncpp
```
python scons.py platform=linux-gcc
```
Lib can be found in `./libs/linux-gcc-4.2.1/libjson_linux-gcc-4.2.1_libmt.a``

