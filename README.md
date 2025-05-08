[![C/C++ CI](https://github.com/keceli/MESS/actions/workflows/build.yml/badge.svg)](https://github.com/keceli/MESS/actions/workflows/build.yml)

# MESS

Master Equation System Solver

The primary purpose of the program is to calculate temperature and pressure dependent
rate coefficients for complex-forming reactions via solution of the one-dimensional master equation. Ancillary calculations of various quantities (e.g., stabilization probabilities for microcanonical initial distributions, microcanonical rate constants, partition functions, and related thermochemical information, time dependent propagation of species populations, etc.) are also available. 

## Building with CMake

Note that this is a fork of the original MESS [repository](https://github.com/Auto-Mech/MESS), to test CMake build and SYCL support for INTEL GPUs. 

Ensure you have CMake (version 3.16 or higher), a C++ compiler (supporting C++11), and a Fortran compiler installed.

1.  **Clone the repository (if you haven't already):**
    ```bash
    git clone https://github.com/keceli/MESS.git
    cd MESS
    ```

2.  **Create a build directory and navigate into it:**
    ```bash
    mkdir build
    cd build
    ```

3.  **Configure the project using CMake:**
    Run CMake from the `build` directory, pointing to the parent directory (where the main `CMakeLists.txt` is located).
    ```bash
    cmake ..
    ```
    This command prepares the build system. By default, it will try to find system libraries and download/build dependencies if they are not found.

    **Build Options (passed to the `cmake ..` command):

    *   `AUTO_DOWNLOAD_DEPENDENCIES` (Default: `ON`): Automatically download and build missing dependencies. To disable, use:
        ```bash
        cmake -DAUTO_DOWNLOAD_DEPENDENCIES=OFF ..
        ```
    *   `USE_SYSTEM_LIBS` (Default: `ON`): Try to use system libraries before downloading. To disable (and force download/build of all dependencies), use:
        ```bash
        cmake -DUSE_SYSTEM_LIBS=OFF ..
        ```
    *   You can combine options: `cmake -DAUTO_DOWNLOAD_DEPENDENCIES=OFF -DUSE_SYSTEM_LIBS=OFF ..`

4.  **Compile the project:**
    After CMake configuration is successful, run `make` (or your chosen build tool like `ninja`) in the `build` directory.
    ```bash
    make -jN # Replace N with the number of parallel jobs you want to use, e.g., make -j4
    ```
    This will compile the MESS executables (mess, mess-v2, messpf, messabs, messsym) and place them in the `build` directory.

## Reference

See Y. Georgievskii, J. A. Miller, M. P. Burke, and S. J. Klippenstein,
Reformulation and Solution of the Master Equation for Multiple-Well Chemical
Reactions, J. Phys. Chem. A, 117, 12146-12154 (2013).

## Acknowledgment

This work was supported by the U.S. Department of Energy, Office of Basic Energy
Sciences, Division of Chemical Sciences, Geosciences, and Biosciences under DOE
Contract Number DE-AC02-06CH11357 as well as the Exascale Computing Project
(ECP), Project Number: 17-SC-20-SC.  The ECP is a collaborative effort of two
DOE organizations, the Office of Science and the National Nuclear Security
Administration, responsible for the planning and preparation of a capable
exascale ecosystem including software, applications, hardware, advanced system
engineering, and early test bed platforms to support the nation's exascale
computing imperative. 

## Notice

Copyright (c) 2018 Yuri Georgievski (ygeorgi@anl.gov), Stephen J.
Klippenstein (sjk@anl.gov), and Argonne National Laboratory.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
