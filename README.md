# Packaging with Spack

Repository for the [Spack exercise](https://github.com/Simulation-Software-Engineering/Lecture-Material/blob/main/building-and-packaging/material/packaging_debian_and_spack_exercise.md)). The code is a slightly modified version of the [code used in the CMake exercise](https://github.com/Simulation-Software-Engineering/cmake-exercise).

The code in this repository does not depend on `deal.ii` anymore to reduce compilation times for the final release. Compared to the CPack part of the exercise you will need `yaml-cpp` version `0.7.0` again so it has to be installed with Spack. Note, that not all releases in this repository need all dependencies. Model this properly in your Spack recipe.

The directory `docker` includes a `Dockerfile` one may use as starting point for the exercise. It will come with Spack preinstalled (but yet completely set up yet). Inside this containe one is not the root user anymore. If you need superuser rights inside the container you can use the `sudo` command.
