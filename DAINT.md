## Testing CUDA 6.5 prerelease on Santis 

### General 
* **????** (LB 13.4.2015) Stressing GPUs. Source available at [this repository](https://github.com/lichinka/cuda-stress) (contact MK).
* **????** Regression tests (contact TWR). 
* Note: MPI over CRAY_CUDA_MPS=1 seems to be broken again, see email from TWR 1 April, 15:42.  FIXED 9 April 2015.
* Note: 6001 and 6003 are failing, this is a simple test that executes libsci_acc DGEMM. FIXED 10 April 2015.

### Applications
* **????** (CG 20.04.2015) _Ramses_ with MPI and OpenACC support, without OpenMP (contact CG).
* **????** _Specfem3D_ exporting CRAY_CUDA_MPS=1. Source available at ``/scratch/santis/lucamar/specfem3d/globe/small_benchmark_run_to_test_very_simple_Earth`` (contact LM and Nina), last test on April 13th successful (jobid=4218).
* **????** _Gromacs_ exporting CRAY_CUDA_MPS=1. Source available at ``/scratch/santis/lucamar/gromacs/driver`` (contact LM and Nina), last test on April 13th successful (jobid=4217).
* **????** _CP2K_ MPI+OpenMP+cuda, version 2.6, exporting CRAY_CUDA_MPS=1. Source available at ``/scratch/santis/lucamar/cp2k/gpu`` (contact LM.) Note: 01.04.2015 MPI over CRAY_CUDA_MPS=1 seems to be broken again, see email from TWR 15:42. Last test on April 13th successful (jobid=4216).
* **FAIL** _BigDFT_ crashes in dcopy when using OpenCL/cuda65. You may find a related ticket [#17793](https://webrt.cscs.ch/Ticket/Display.html?id=17793).

### Ticket-related tests
* **????** (GPP 10.04.2015) [#15166](https://webrt.cscs.ch/Ticket/Display.html?id=15166): nvcc warning no longer appears (contact LB).
* **????** (GPP 10.04.2015) [#17365](https://webrt.cscs.ch/Ticket/Display.html?id=17365): G2G over MPI with CUDA and OpenCL working ok (contact LB).
* **????** (GPP 10.04.2015) [#17402](https://webrt.cscs.ch/Ticket/Display.html?id=17402): basic profiling by exporting COMPUTE_PROFILE=1 (contact LB).
* **????** (GPP 10.04.2015) [#17591](https://webrt.cscs.ch/Ticket/Display.html?id=17591): DGEMM status error when exporting CRAY_CUDA_MPS=1 no longer occurs (contact LB).
* **????** (GPP 10.04.2015) [#17988](https://webrt.cscs.ch/Ticket/Display.html?id=17988): problem solved with if using module ``cray-libsci_acc/3.1.1``. The related CrayPort bug is [#802506](https://crayport.cray.com/_layouts/cray.portal.bugs/BugDetails.aspx?BugId=821506) (contact AJ).
* Source code available at [this repository](https://github.com/lichinka/L2).


### OpenCL (contact LB)
* **????** (LB 13.4.2015) OpenCL 1.0/1.1 tests working ok.
* **????** (LB 13.4.2015) G2G over MPI tests working ok.
* Source available at [this repository](https://github.com/lichinka/opencl-training).


### C++11 support
* **????** (LB 13.4.2015) GridTools compilation fails if using the ``CC`` wrapper to compile CUDA code, which passes the ``-mavx`` to the ``nvcc`` compiler. The workaround for ``g++ 4.8.2`` is to avoid passing the ``-mavx`` option to ``nvcc``. Another workaround is to use ``g++ 4.7.3`` (contact MB).
* A ticket has been opened to track this issue with Cray (see ticket [#19002](https://webrt.cscs.ch/Ticket/Display.html?id=19002) for full description and test case).


### COSMO
* **????** (LB 10.4.2015) Xavier successfully compiled and run COSMO tests using CCE and CUDA 6.5 ( see ticket [#18018](https://webrt.cscs.ch/Ticket/Display.html?id=18018) ).


### Visualization
There is no direct dependency between the visualization tools and CUDA. Only through the driver update affects them due to OpenGL support.
* **????** (GF 13.4.2015) Xorg recompilation with the lastest Nvidia driver was successful (contact GF).
* **????** (GF 13.4.2015) No outstanding issues after latest recompilation (contact GF).

### JG
#### PE
* **????** 2015/04/09 ``cuda/6.5`` [matrixMulCUBLAS](https://bitbucket.org/jgphpc/pug/issue/27/matrixmulcublas)

#### Debugging
* **????** 2015/04/09 ddt/5.0 [matrixMulCUBLAS](https://bitbucket.org/jgphpc/pug/issue/27/matrixmulcublas)

#### Profiling
* **????** ``perftools+cp2k`` [cp2k+cuda+gnu](https://bitbucket.org/jgphpc/pug/issue/24/cp2k). (Issue with hugepage ?)
* **????** ``scorep`` [jacobi+mpi+cuda](https://bitbucket.org/jgphpc/pug/issue/7/jacobi-mpi-cuda)
* **???? with WORKAROUND** 2015/04/15 ``nvprof``: libcuinj64.so => ticket [#18909/823648](https://webrt.cscs.ch/Ticket/Display.html?id=18909)

### AJ
* **????** 2015/04/13 pic_engine compiles and runs | Fortran code with OpenACC and a few kernals in CUDA C
