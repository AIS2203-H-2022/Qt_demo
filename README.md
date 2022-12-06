# Qt Demo

When building using CMake on the command line or using CLion (i.e. not using Qt Creator) two thing are needed:

1. Add `C:\Qt\<version>\msvc2019_64\bin` to PATH
2. Append `-DCMAKE_PREFIX_PATH=C:\Qt\<version>\msvc2019_64` to the CMake command
