## Testing CUDA 6.5 prerelease on Daint

### General 
* **PASS** (LB 13.5.2015) Stressing GPUs. Source available at [this repository](https://github.com/lichinka/cuda-stress).
* **PASS** (TWR 12.5.2015) Regression tests.

### Applications
* **????** (CG 20.04.2015) _Ramses_ with MPI and OpenACC support, without OpenMP (contact CG).
* **PASS** _Specfem3D Globe_ MPI exporting CRAY_CUDA_MPS=1 (contact LM)
* **PASS** _Gromacs_ MPI+OpenMP+cuda, version 5.0.4, exporting CRAY_CUDA_MPS=1 (contact LM) 
* **PASS** _CP2K_ MPI+OpenMP+cuda, version 2.6, exporting CRAY_CUDA_MPS=1 (contact LM)
* **????** _BigDFT_ crashes in dcopy when using OpenCL/cuda65. You may find a related ticket [#17793](https://webrt.cscs.ch/Ticket/Display.html?id=17793).

### Ticket-related tests
* **PASS** (LB 12.05.2015) [#15166](https://webrt.cscs.ch/Ticket/Display.html?id=15166): nvcc warning no longer appears.
* **PASS** (LB 12.05.2015) [#17365](https://webrt.cscs.ch/Ticket/Display.html?id=17365): G2G over MPI with CUDA and OpenCL working ok.
* **PASS** (LB 12.05.2015) [#17402](https://webrt.cscs.ch/Ticket/Display.html?id=17402): basic profiling by exporting COMPUTE_PROFILE=1.
* **PASS** (LB 12.05.2015) [#17591](https://webrt.cscs.ch/Ticket/Display.html?id=17591): DGEMM status error when exporting CRAY_CUDA_MPS=1 no longer occurs.
* **PASS** (LB 12.05.2015) [#17988](https://webrt.cscs.ch/Ticket/Display.html?id=17988): problem solved with if using module ``cray-libsci_acc/3.1.1``. The related CrayPort bug is [#802506](https://crayport.cray.com/_layouts/cray.portal.bugs/BugDetails.aspx?BugId=821506).
* The complete source code for these tests is available at [this repository](https://github.com/lichinka/L2).


### OpenCL (contact LB)
* **PASS** (LB 12.5.2015) OpenCL 1.0/1.1 tests working ok.
* **PASS** (LB 12.5.2015) G2G over MPI tests working ok.
* The complete source code for these tests is available at [this repository](https://github.com/lichinka/opencl-training).


### C++11 support
* **FAIL** (LB 13.4.2015) GridTools compilation fails if using the ``CC`` wrapper to compile CUDA code, which passes the ``-mavx`` to the ``nvcc`` compiler. The workaround for ``g++ 4.8.2`` is to avoid passing the ``-mavx`` option to ``nvcc``. Another workaround is to use ``g++ 4.7.3`` (contact MB).
* A ticket has been opened to track this issue with Cray (see ticket [#19002](https://webrt.cscs.ch/Ticket/Display.html?id=19002) for full description and test case).


### COSMO
* **????** (LB 10.4.2015) Xavier successfully compiled and run COSMO tests using CCE and CUDA 6.5 ( see ticket [#18018](https://webrt.cscs.ch/Ticket/Display.html?id=18018) ).


### Visualization
There is no direct dependency between the visualization tools and CUDA. Only through the driver update affects them due to OpenGL support.
* **PASS** (JF 12.5.2015) Xorg recompilation with the lastest Nvidia driver was successful.
* **PASS** (JF 12.5.2015) No outstanding issues after latest recompilation.

### JG
#### PE
* **PASS** 2015/05/21 ``cuda/6.5`` [matrixMulCUBLAS](https://bitbucket.org/jgphpc/pug/issue/27/matrixmulcublas)

#### Debugging
* **PASS** 2015/05/21 ddt/5.0 [matrixMulCUBLAS](https://github.com/eth-cscs/parallel-debuggers/issues/51)

#### Profiling
* **PASS** ``scorep/141`` 2015/05/21[jacobi+mpi+cuda](https://bitbucket.org/jgphpc/pug/issue/7/jacobi-mpi-cuda)
* **PASS (with WORKAROUND)** 2015/05/21 ``nvprof``: libcuinj64.so => ticket [#18909/823648](https://webrt.cscs.ch/Ticket/Display.html?id=18909)
* **PASS** 2015/05/27 ``perftools+cp2k`` [cp2k+cuda+gnu](https://bitbucket.org/jgphpc/pug/issue/24/cp2k).
 
### AJ
* **????** 2015/04/13 pic_engine compiles and runs | Fortran code with OpenACC and a few kernals in CUDA C
