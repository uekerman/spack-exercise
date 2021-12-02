# Packaging with Spack

Repository for the [Spack exercise](https://github.com/Simulation-Software-Engineering/Lecture-Material/blob/main/building-and-packaging/material/packaging_debian_and_spack_exercise.md). The code is a slightly modified version of the [code used in the CMake exercise](https://github.com/Simulation-Software-Engineering/cmake-exercise).

The code in this repository does not depend on `deal.ii` anymore to reduce compilation time for the final release. Compared to the CPack part of the exercise, you need `yaml-cpp` version `0.7.0` again. It has to be installed with Spack. Note, that not all releases in this repository need all dependencies. Model this properly in your Spack recipe.

The directory `docker` includes a `Dockerfile` one may use as starting point for the exercise. It comes with Spack preinstalled (but not yet completely set up yet). Inside the container, one is not the root user anymore. If you need superuser rights inside the container, you can use the `sudo` command.
