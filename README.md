## HDF5 Windows Libraries as used by the [**h5**](https://github.com/mannau/h5) R-Package

### COMPILATION

**PREQUISITES**  
  The Library has been compiled using Windows 7 64Bit using the following tools:
  - Rtools 3.3, see http://cran.r-project.org/bin/windows/Rtools
  - CMake, current version (e.g. 3.2.1, installed using standard parameters), see http://www.cmake.org/download
  - HDF5 1.8.17 obtained from http://www.hdfgroup.org/ftp/HDF5/current/src/hdf5-1.8.17.tar.gz, 
    unpack to e.g. C:\hdf5

**BUILD STEPS**
  1. Check if Rtools Windows Environment PATH variables are set accordingly, i.e.
    - For 32Bit Platforms: C:\Rtools\bin;C:\Rtools\mingw_32\bin
    - For 64Bit Platforms: C:\Rtools\bin;C:\Rtools\mingw_64\bin
  2. Open CMake Gui, set CMake Source dir to HDF5 Source, e.g. C:\hdf5; Set build dir to new 
    directory, push button "Configure".
    - For 32Bit Platforms:
      + gcc dir: C:/Rtools/mingw_32/bin/gcc.exe
      + g++ dir: C:/Rtools/mingw_32/bin/g++.exe
    - For 64Bit Platforms: 
      + gcc dir: C:/Rtools/mingw_64/bin/gcc.exe
      + g++ dir: C:/Rtools/mingw_64/bin/g++.exe
  3. The following parameters need to be set manually in the CMake tool (check Advanced Box):
    * BUILD_SHARED_LIBS: uncheck
    * BUILD_STATIC_EXECS: check
    * CMAKE_BUILD_TYPE: Release
    * HDF5_BUILD_CPP_LIB: check
    * HDF5_BUILD_HL_LIB: check
    * HDF5_BUILD_TOOLS: uncheck
    * HDF5_ENABLE_ZLIB_SUPPORT: check
    * Set ZLIB
      - For 32Bit Platforms:
        + ZLIB_INCLUDE_DIR: C:/Rtools/mingw_32/i686-w64-mingw32/include
        + ZLIB_LIBRARY: C:/Rtools/mingw_32/i686-w64-mingw32/lib/libz.a
      - For 64Bit Platforms:
        + ZLIB_INCLUDE_DIR: C:/Rtools/mingw_64/x86_64-w64-mingw32/include
        + ZLIB_LIBRARY: C:/Rtools/mingw_64/x86_64-w64-mingw32/lib/libz.a
  4. After Configuration is finished change to build-dir and compile using
    $ mingw32-make
