# Python environment set up


## 개념 정리
### What is Conda?
[Conda](https://docs.conda.io/en/latest/)는
> *Package, dependency and environment management for any language*—Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, Fortran, and more.  
> Conda is an open source package management system and environment management system that runs on Windows, macOS, and Linux.  

여러 가지의 개발 환경을 관리하기 좋은 package management이다. Python의 패키지 관리를 가상환경 설정을 통해서 쉽게 할 수 있다.

### Conda, Anaconda, Miniconda
Conda와 같이 나오는 여러 개념들을 다음과 같이 정리했다.
- **`Conda`**: 패키지 매니저로 `Anaconda`와 `Miniconda` 두 가지가 있다.
- **`Anaconda`**: Conda + Python + other scientific computing packages가 전부 포함 (용량이 큼)
- **`Miniconda`**: Conda + Python + 필수 패키지만 (Anaconda의 minimal 버전, 용량이 작음)

### Conda channel
Conda channel은 패키지들이 저장된 곳이며, conda는 conda channel을 통해서 패키지를 다운받는다. 보통의 경우 기본 channel은 [`Anaconda default channel`](https://repo.anaconda.com/pkgs/)이다. `conda-forge`는 community에 의해 관리되는 패키지 collection이며, 더욱 다양하고 최신 버전의 패키지 repo이다.

- **Miniforge**: Community driven miniconda라 생각하면 된다. 패키지 설치를 `conda-forge` channel을 통해 한다. (`Miniconda`는 anaconda channel 사용)

### 결론은 Mambaforge를 사용하자!
- **`Mamba`**, **`Mambaforge`**: `Conda`를 C++로 만든 것으로 패키지 설치 등이 훨씬 빠른 장점이 있다. 장점이 많기 때문에 `mamba`를 사용하면 된다. Conda-forge가 default channel이다.


## Mamba 설치 및 설정
Mambaforge를 이용하여 python 가상 환경 설치 방법 정리

### 링크 모음
- [Mamba's documentation](https://mamba.readthedocs.io/en/latest/index.html)
- [Mamba installation](https://mamba.readthedocs.io/en/latest/installation.html)
- [Mambaforge download](https://github.com/conda-forge/miniforge#mambaforge)
- [Tutorial: Setting up Python enviroments with Mambaforge](https://ross-dobson.github.io/posts/2021/01/setting-up-python-virtual-environments-with-mambaforge/)  
- [Installing Anaconda packages more quickly using Mamba](https://blog.hpc.qmul.ac.uk/mamba.html)


### 설치
1. Github 링크 [Mambaforge download](https://github.com/conda-forge/miniforge#mambaforge)에 접속해 Mambaforge에서 자신에게 해당하는 OS, Architecture 본 후 다운로드 (flatland는 Linux x86_64 (amd64), Mac Studio는 OS X arm64 (Apple Silicon) 선택)  
2. 다운로드 후, ftp를 이용하여 서버 컴퓨터로 옮긴 후, 
```console
bash Mambaforge-$(uname)-$(uname -m).sh
```
3. Do you wish the installer to initialize Mambaforge by running conda init?에서 yes 선택 (conda가 자동으로 mambaforge에 연결 되도록 함)
4. Terminal 재접속 하면 username 왼쪽에 (base)라고 뜸 (현재 base 가상환경이 선택 되었다는 것을 나타냄)

## 가상 환경 설정
Conda (Mambaforge지만 사실상 conda와 같기 때문에, 아래에서 conda로 부르겠음)에는 default 가상 환경인 `base`가 존재한다.  
***`base`에서 절대 새로운 패키지를 설치하지 말고, 새로운 가상 환경을 만들어서 Python, 패키지 등을 설치하고 관리하자!***

**가상 환경 만들기**  
설치 3에서 yes를 선택했다면 `mamba` 대신 `conda`를 입력해도 됨.
```shell
mamba create -n <envname> python=3.xx
```

**가상 환경 보기**
```shell
mamba env list
```

**가상 환경 삭제**
```shell
mamba env remove -n <envname>
```

**Install package**
```shell
mamba install <package1_name>=<version>, <package2_name>=<version>, ...
```
예시) Python 3.10 설치 `mamba install python=3.10`  
패키지 버전을 입력하지 않으면 자동으로 최신 버전을 설치함 (`mamba install python` 가능)

**Search package**
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


## SSH 접속시 Conda environment 자동 선택
`.bashrc`에 `source activate <envname>` 
