## Jupyter running latest Pytorch on GPU using cuDNN 

#### To use

```
mkdir notebooks

nvidia-docker run -it -p 8888:8888 -d -v notebooks:/notebooks yogesh211/jupyter-pytorch-gpu
```