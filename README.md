# `GNES` docker images

## Build, run and push a container


## Internal available images

| Name | Description |
|---|---|
|[`gnes/build-base:latest` (base/Dockerfile)](./base/Dockerfile)  | GPU python 3.6.8 cuda-10.0 tf1.14 pytorch1.1 faiss|
|[`gnes/build-base:cuda9.0` (base/Dockerfile)](https://github.com/gnes-ai/docker/blob/cuda9/base/Dockerfile)  | GPU python 3.6.8 cuda-9.0 tf1.12 pytorch1.1 faiss|
|[`gnes/ci-base:latest` (ci-base/Dockerfile)]((./ci-base/Dockerfile))   | build on `gnes/build-base:latest`, used in CI |

