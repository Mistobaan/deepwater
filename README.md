# Deep Water

Native implementation of Deep Learning models for GPU backends (mxnet, Caffe, TensorFlow, etc.)

![architecture](./architecture/overview.png "Deep Water High-Level Architecture")

## Build Requirements

1. A C++ compiler with C++11 support
1. [SWIG](http://www.swig.org/)
1. [BLAS](http://www.netlib.org/blas/)
1. [OpenCV](http://opencv.org)

### Ubuntu

```bash
sudo apt-get install libatlas-base-dev libblas-dev libopencv-dev swig -y
git clone https://github.com/h2oai/deepwater.git
git submodule update --init --recursive
cd mxnet
make
cd ..
make
make pkg # will generate a `jar` file including native code.
```

Please add these lines below into your Java code when using this jar as external dependency.

```Java
util.loadCudaLib();
util.loadNativeLib("mxnet");
util.loadNativeLib("Native");
```

An example implementation can be found in [H2O](https://github.com/h2oai/h2o-3/blob/deepwater/h2o-algos/src/test/java/hex/deeplearning/DeepWaterTest.java).
