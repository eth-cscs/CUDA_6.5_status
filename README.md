## Testing CUDA 6.5 prerelease on Santis 

### General 
* **PASS** Stressing GPUs. Source available at [this repository](https://github.com/lichinka/cuda-stress) (contact MK).
* **PASS** Regression tests (contact TWR). Note: 01.04.2015 MPI over CRAY_CUDA_MPS=1 seems to be broken again, see email from TWR 15:42. Thi sis now fixed. But... 6001 and 6003 are FAILING. These tests libsci_acc DGEMM.

### Applications
* **PASS** _Ramses_ with MPI and OpenACC support, without OpenMP (contact CG).
* **PASS** _Specfem3D_ exporting CRAY_CUDA_MPS=1. Source available at ``/scratch/santis/lucamar/specfem3d/globe`` (contact LM and Nina).
* **PASS** _Gromacs_ exporting CRAY_CUDA_MPS=1. Source available at ``/scratch/santis/lucamar/gromacs`` (contact LM and Nina).
* **PASS** _CP2K_ MPI+OpenMP+cuda, version 2.6, exporting CRAY_CUDA_MPS=1. Source available at ``/scratch/santis/lucamar/cp2k/gpu`` (contact LM.) Note: 01.04.2015 MPI over CRAY_CUDA_MPS=1 seems to be broken again, see email from TWR 15:42.

### Ticket-related tests
* **PASS** [#15166](https://webrt.cscs.ch/Ticket/Display.html?id=15166): nvcc warning no longer appears (contact LB).
* **PASS** [#17365](https://webrt.cscs.ch/Ticket/Display.html?id=17365): G2G over MPI with CUDA and OpenCL working ok (contact LB).
* **PASS** [#17402](https://webrt.cscs.ch/Ticket/Display.html?id=17402): basic profiling by exporting COMPUTE_PROFILE=1 (contact LB).
* **PASS** [#17591](https://webrt.cscs.ch/Ticket/Display.html?id=17591): DGEMM status error when exporting CRAY_CUDA_MPS=1 no longer occurs (contact LB).
* **FAIL** [#17988](https://webrt.cscs.ch/Ticket/Display.html?id=17988): OpenACC initialization fails on ``libsci_acc_init();`` if using module ``cray-libsci_acc/3.1.1``. However, the related CrayPort bug is marked as solved ( see [#802506](https://crayport.cray.com/_layouts/cray.portal.bugs/BugDetails.aspx?BugId=821506) ) (contact AJ).
* Source code available at [this repository](https://github.com/lichinka/L2).


### OpenCL (contact LB)
* **PASS** OpenCL 1.0/1.1 tests working ok.
* **PASS** G2G over MPI tests working ok.
* Source available at [this repository](https://github.com/lichinka/opencl-training).


### C++11 support
* **PASS** GridTools compilation fails if using the ``CC`` wrapper to compile CUDA code, which passes the ``-mavx`` to the ``nvcc`` compiler. The workaround for ``g++ 4.8.2`` is to avoid passing the ``-mavx`` option to ``nvcc``. Another workaround is to use ``g++ 4.7.3`` (contact MB).
* A minimal test case follows:
```c++
#include <algorithm>

int main (int argc, char **argv)
{
    return EXIT_SUCCESS;
}
```
* Compile on Santis with:
```
$> module load cudatoolkit
$> nvcc -ccbin /opt/gcc/4.8.2/bin/g++ -std=c++11 test.cu                        # Works
$> nvcc -ccbin /opt/gcc/4.8.2/bin/g++ -std=c++11 test.cu -Xcompiler ,\"-mavx\"  # FAILS
$> nvcc -ccbin /opt/gcc/4.7.3/bin/g++ -std=c++11 test.cu -Xcompiler ,\"-mavx\"  # Works
```


### COSMO
* **????** Xavier and Carlos have been given access to Santis in order to compile COSMO with CCE and CUDA 6.5 ( see ticket [#18018](https://webrt.cscs.ch/Ticket/Display.html?id=18018) ).


### Profiling
* **????** ``perftools`` on CP2K + CUDA working ok. Setup and instructions are available [here](https://bitbucket.org/jgphpc/pug/issue/24/cp2k), but are not yet reproducible (contact JG).
* **????** ``scorep``: installation + test still ongoing (contact JG).


### Debugging
* **????** ddt/5.0 is working after Allinea's intervention. Still waiting for a reproducible test case (contact JG).


### Visualization
There is no direct dependency between the visualization tools and CUDA. Only through the driver update affects them due to OpenGL support.
* **PASS** Xorg recompilation with the lastest Nvidia driver was successful (contact GF).
* **PASS** Testing of visualization tools has been performed and they are working ok (contact GF).

### JG
* **PASS** 2015/04/09 [matrixMulCUBLAS](https://bitbucket.org/jgphpc/pug/issue/27/matrixmulcublas)

