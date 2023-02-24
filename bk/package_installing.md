# Package Installation on Linux 

## From Source Code

### Proj 9.1.0
  
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
### ncdf4 (R package) & netcdf-c-4.9.1

  Normal configuration and make and make install.
  One thing has to be noticed is that if you wish to share your package to other users, please `setfacl -m g::r-x (netcdf-c library files)`.
  

## Installing particular R packages

### Monocle3
  
  ```
  BiocManager::install(c('BiocGenerics', 'DelayedArray', 'DelayedMatrixStats',
                       'limma', 'lme4', 'S4Vectors', 'SingleCellExperiment',
                       'SummarizedExperiment', 'batchelor', 'HDF5Array',
                       'terra', 'ggrastr'))
  devtools::install_github('cole-trapnell-lab/monocle3')
  ```
  
  Package `terra` requires `GDAL` and `GDAL` requires `PROJ`.
  
  
