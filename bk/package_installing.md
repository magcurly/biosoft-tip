# Package Installation on Linux 

## From Source Code

### Proj-910
  
  I found a crash on I/O Error during `make`. I am unable to find a way to solve it. Bypassing the compiling step, using pre-compiling PROJ tar.gz from Conda repository and copy everything in bin/lib/include/share to the target installation directory.
 
### GDAL 3.6.0

  Using the minimal installation way and designating the CMAKE path and target directory will make it happend.

```
mkdir build & cd build
cmake -DGDAL_BUILD_OPTIONAL_DRIVERS=OFF -DOGR_BUILD_OPTIONAL_DRIVERS=OFF \
-DCMAKE_PREFIX_PATH=/path/to/your/cmake \
-DCMAKE_INSTALL_PREFIX=/path/to/your/installation/directory ..
cmake --build .
cmake --build . --target install
```
