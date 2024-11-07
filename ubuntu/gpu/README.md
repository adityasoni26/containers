# GPU Containers

**WARNING**: Using conda in DCS images is no longer supported starting Databricks Runtime 9.0. We highly recommend users to extend [`cuda-11.8`](cuda-11.8) examples.
 We no longer support [`cuda-10.1`](cuda-10.1) and [`cuda-11.0`](cuda-11.0) compatibility with latest databricks runtime.

**WARNING**: DCS images which extends [`venv`](cuda-11.8/venv/) need to be paired with DBR 14.x when creating a
cluster. In order for REPL to launch successfully, the python packages used in the image HAVE to match with python packges used in the paried DBR version. [`venv`](cuda-11.8/venv/) uses version set from DBR 14.0


There are three variations of GPU containers that can be used depending upon the CUDA version you wish to use:
- [`cuda-11.8`](cuda-11.8) contains the layers which install CUDA 11.8
- [`cuda-11.0`](cuda-11.0)(*Deprecated*) contains the layers which install CUDA 11.0
- [`cuda-10.1`](cuda-10.1)(*Deprecated*) contains the layers which install CUDA 10.1

 
Example base layers to build your own container:
* [`gpu-base`](cuda-11.0/base) extends the official [NVIDIA CUDA container](https://hub.docker.com/r/nvidia/cuda) with Databricks Container Service minimal requirements.
* [`gpu-venv`](cuda-11.8/venv) extends `gpu-base` by installing cuda dependencies and commmon Databricks python dependencies in venv.

Example containers for common GPU use cases:
* [`gpu-tensorflow`](cuda-11.8/tensorflow) extends `gpu-venv` by creating a conda environment that contains [TensorFlow](https://www.tensorflow.org/).
* [`gpu-pytorch`](cuda-11.8/pytorch) extends `gpu-venv` by creating a conda environment that contains [PyTorch](https://pytorch.org/).

## Launching GPU Clusters
* After the cluster is ready, you can run `%sh nvidia-smi` to view GPU devices and confirm that they are available.

## Creating Custom Dockerfiles:

* You can modify the `gpu-base` Dockerfile and add additional system packages and NVIDIA libraries, for example, TensorRT (libnvinfer).

* You cannot change the NVIDIA driver version, because it must match the driver version on the host machine, which is 450.80.

* The `gpu-tensorflow` and `gpu-pytorch` Dockerfiles provide examples to create the root conda environment from an environment.yml file. These packages are required for Python notebooks and PySpark to work: python, ipython, numpy, pandas, pyarrow, six, and ipykernel.
