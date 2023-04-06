# Python environment set up

Mambaforge를 이용하여 python 가상 환경 설치 방법 정리

[Mamba's documentation](https://mamba.readthedocs.io/en/latest/index.html)

[Tutorial: Setting up Python enviroments with Mambaforge](https://ross-dobson.github.io/posts/2021/01/setting-up-python-virtual-environments-with-mambaforge/)  

## Why Mamba?
Mamba는 conda보다 package 설치가 훨씬 빠름  
https://blog.hpc.qmul.ac.uk/mamba.html


## Mambaforge 설치
설치 방법  
https://mamba.readthedocs.io/en/latest/installation.html

Mambaforge Download  
https://github.com/conda-forge/miniforge#mambaforge

conda-forge가 default channel

## 가상 환경 설정
**가상 환경 만들기**
```shell
mamba create -n <envname> python=3.xx
```

**가상 환경 삭제**
```shell
mamba env remove -n <envname>
```

**Install package**
```shell
mamba search <package_name>
```
**Rename env**
```shell
mamba env update --name <old_name> --name <new_name>
```


## Python, Numpy 설치 순서대로
```shell
mamba create -n <envname> python=3.xx
```

```shell
mamba install numpy
```
