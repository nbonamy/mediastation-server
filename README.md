# mediastation-server

## Compiling external libs

### Prerequisite

On MacOS 10.9+ it is necessary to install https://docs.brew.sh/C++-Standard-Libraries.

### zlib
```
make
```
Lib can be found in `./libz.a`.


### curl
```
export MACOSX_DEPLOYMENT_TARGET="10.6"
./configure --disable-shared --enable-static
make
```
Lib can be found in `./lib/.libs/libcurl.a`.

### jpeglib
```
./configure --disable-shared --enable-static
```
Edit the `Makefile` to add `$(TROBJECTS)` to `libjpeg.a` and `libjpeg.la` rules (as dependencies and sources).
```
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

#### Linux
```
./configure
make
```
#### MacOS
```
./configure -with-CC=/usr/local/Cellar/gcc@7/7.4.0_2/bin/gcc-7
make
```
Lib can be found in `./libtiff/libtiff.a`.

### ptypes
```
make
```
Lib can be found in `./lib/libtypes.a`.

### tinyxml
```
make
```
Lib can be found in `./libtinyxml.a`.

### taglib

#### Linux
```
cmake -DCMAKE_BUILD_TYPE=Release -DENABLE_STATIC=ON .
make
```

#### MacOS
```
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_C_COMPILER=/usr/local/Cellar/gcc@7/7.4.0_2/bin/gcc-7 -DCMAKE_CXX_COMPILER=/usr/local/Cellar/gcc@7/7.4.0_2/bin/g++-7 -DENABLE_STATIC=ON .
make
```

Lib can be found in `./taglib/libtag.a`.

### boost
```
./configure
make
```

On MacOS, edit `user-config.jam` before `make` and set `gcc`:
```
using gcc : 7 : /usr/local/Cellar/gcc@7/7.4.0_2/bin/g++-7 ;
```


### miniupnpc
```
make
```
Lib can be found in `./libminiupnpc.a`.

### jsoncpp
```
python scons.py platform=linux-gcc
```
Lib can be found in `./libs/linux-gcc-4.2.1/libjson_linux-gcc-4.2.1_libmt.a`.

### ffmpeg

#### Prerequisites
```
sudo apt-get install libmp3lame-dev libtheora-dev libva-dev libvdpau-dev libvorbis-dev libgsm1-dev zlib1g-dev
```

#### Xvid
```
wget http://downloads.xvid.org/downloads/xvidcore-1.3.3.tar.gz
tar xzvf xvidcore-1.3.3.tar.gz
cd xvidcore/build/generic
./configure --prefix=/usr/local
make
sudo make install
```

#### x264
```
git clone git://git.videolan.org/x264.git
cd x264
./configure --prefix=/usr/local --enable-static --disable-opencl
make
sudo make install
```

#### ffmpeg
```
./configure --extra-ldflags="-L/usr/local/lib -L/usr/lib/x86_64-linux-gnu" --enable-gpl --disable-static --enable-shared --disable-programs --disable-encoders --disable-filters --disable-muxers --disable-bsfs --disable-protocols --disable-devices --disable-doc --disable-avdevice --disable-swresample --disable-avresample --disable-swscale --disable-postproc --disable-avfilter --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libxvid --enable-libx264
```
Libs can be found in (remove number when copying):
  - `./libavformat/libavformat.so.58` 
  - `./libavcodec/libavcodec.a.58`
  - `./libavutil/libavutil.a.56`
  

