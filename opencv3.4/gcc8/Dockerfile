FROM stal12/ubuntu18-gcc8

WORKDIR /home

# Installare git, gcc, make e cmake
# Sono nell'immagine padre

# Install opencv-3.4.6 with selected modules
RUN apt-get update && apt-get install -y wget \
    && wget https://github.com/opencv/opencv/archive/3.4.6.tar.gz \
    && tar -xvzf 3.4.6.tar.gz opencv-3.4.6 \
    && rm 3.4.6.tar.gz \
    && cd opencv-3.4.6 \
    && mkdir gcc8_static_bin \
    && cd gcc8_static_bin \
    && cmake \
        -D BUILD_SHARED_LIBS=OFF \
        -D CMAKE_INSTALL_PREFIX=`pwd`/install \
        -D BUILD_LIST=core,imgproc,imgcodecs,photo \
        -D BUILD_opencv_java_bindings_generator=OFF \
        -D BUILD_opencv_python3=OFF \
        -D BUILD_opencv_python_bindings_generator=OFF \
        -D BUILD_opencv_python_tests=OFF \
        -D BUILD_JPEG=ON \
        -D BUILD_PNG=ON \
        -D BUILD_TIFF=ON \
        -D BUILD_DOCS=OFF \
        -D BUILD_TESTS=OFF \
        -D BUILD_PERF_TESTS=OFF \
        -D CMAKE_BUILD_TYPE=Release \
        -D INSTALL_C_EXAMPLES=OFF \
        -D INSTALL_PYTHON_EXAMPLES=OFF \
        .. \
    && cmake --build . -j7 \
    && cmake --build . --target install
    
ENV OpenCV_DIR=/home/opencv-3.4.6/gcc8_static_bin
