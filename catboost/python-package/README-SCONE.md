# Build

## Prerequesites

* Docker
* Docker must be logged in to registry.scontain.com:5050

## Build script

```
export BUILD_DIR=/opt/catboost 
mkdir -p $BUILD_DIR &&
git clone https://github.com/Super-Protocol/catboost $BUILD_DIR &&
docker run -it -v $BUILD_DIR:/catboost -it registry.scontain.com:5050/sconecuratedimages/crosscompilers sh -c 'apk add yasm && cd /catboost/catboost/python-package && SCONE_FORK=1 /usr/bin/python3 mk_wheel.py -DUSE_ARCADIA_PYTHON=no -DUSE_SYSTEM_PYTHON=3.7 -DHAVE_CUDA=no --build-widget=no --c-compiler=/usr/local/bin/scone-gcc --cxx-compiler=/usr/local/bin/scone-g++'
```
