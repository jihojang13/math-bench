# Linear Algebra Libraries
Linear algebra 연산에 쓰이는 libraries, implementations에 대한 용어 정리

### 추가 예정 내용

## 목차
1. [BLAS](#BLAS)
1. [LAPACK](#LAPACK)
1. [BLAS/LAPACK implementation](#BLAS/LAPACK-implementation)
1. [BLAS/LAPACK implementation 고르기](#BLAS/LAPACK-implementation-고르기)

---

## BLAS
BLAS (**B**asic **L**inear **A**lgebra **S**ubprograms)는 low-level linear algebra 연산 (matrix multiplication, vector addition, dot products, ...)을 하기 위한 library이다. Linear algebra 연산의 사실상 표준으로 여겨진다.

## LAPACK
LAPACK (**L**inear **A**lgebra **Pack**age)은 higher-level linear algebra의 연산 (solving linear equation, eigenvalue problem, singular value decomposition, ...)을 하기 위한 library이다. BLAS를 사용하여 연산을 한다.

## BLAS/LAPACK implementation
BLAS, LAPACK을 다양한 CPU, GPU 등에 최적화 시켜 implement한 것을 사용하게 되는데, 아래 세 개가 우리가 접할 대표적인 implementations이다.

- [OpenBLAS](https://en.wikipedia.org/wiki/OpenBLAS)  
Open-source implementation of the BLAS and LAPACK.

- [MKL (Math Kernel Library)](https://en.wikipedia.org/wiki/Math_Kernel_Library)  
Intel에서 만든 BLAS, LAPACK, fast Fourier transfomrs 등을 포함한 math library.

- [Accelerate](https://developer.apple.com/documentation/accelerate)  
Apple에서 만든 BLAS, LAPACK 등 다양한 연산을 포함한 library.

**[⬆ 위로 돌아가기](#목차)**

---

## BLAS/LAPACK implementation 고르기
C++의 Eigen, Python의 numpy, julia의 내장 linear algebra 함수 등은 BLAS/LAPACK implementation 중 하나를 사용하며, 어떤 implementation을 사용할지 변경 할 수 있다. 각 CPU마다 가장 좋은 효율을 낼 수 있는 implementation 이 다르기 때문에, 적절한 선택을 통해 최적화를 시키는 것이 중요하다. 


**[⬆ 위로 돌아가기](#목차)**
