# How to install the OpenCL SDK

In general, refer to common practices for your platform. This page here collects first pointers and common guides.

It is possible that SDKs come with the runtimes of various vendors. However, development is tested
against the official [Khronos OpenCL SDK](https://github.com/KhronosGroup/OpenCL-SDK).

For all approaches, the repositories expect to find the headers in system include folder `CL/` (and `OpenCL/` for Apple); for example, `#include <CL/cl.h>`.
Linkage is performed against library (or Apple framework) `OpenCL`. 

## Microsoft Windows

For Microsoft Windows, use to the released packages from [Khronos OpenCL SDK](https://github.com/KhronosGroup/OpenCL-SDK).

* Download the latest binary release from [the list of releases](https://github.com/KhronosGroup/OpenCL-SDK/releases).
  * It is either the `OpenCL-SDK-vYYYY.MM.DD-Win-x64.zip` or `OpenCL-SDK-vYYYY.MM.DD-Win-x32.zip` - depending on your intended architecture.
* Unpack the contained header and library files into a dedicated directory. For example `D:\OpenCL\Khronos\...`
* Ensure the header and library files can be found by the compiler and linker.
  * For example, use `Edit the system environment variables` in Windows to extend the "User variables". For example:
  * `CGO_CFLAGS=-ID:\OpenCL\Khronos\include`
  * `CGO_CPPFLAGS=-ID:\OpenCL\Khronos\include`
  * `CGO_CXXFLAGS=-ID:\OpenCL\Khronos\include`
  * `CGO_LDFLAGS=-LD:\OpenCL\Khronos\lib`

## Linux

For Linux, it depends on the distribution.

For Debian-based systems, there are readily-available packages for the official SDKs. 
On Ubuntu-22.04 (or later), you can run the following commands:
```
sudo apt-get update
sudo apt-get install opencl-headers ocl-icd-opencl-dev
```

> The GitHub workflow CI scripts of the repositories perform the steps on such a system.

> Earlier distribution versions may also provide these packages, yet in an older version.
> This will then decide which OpenCL API level - and Go wrapper - you can use and develop against.

## Apple MacOS

Apple has discontinued support for OpenCL after version 1.2.
As such, only the [opencl-go/cl12](https://github.com/opencl-go/cl12) repository is compatible with such a system.

However, the OpenCL SDK should be pre-installed on a system. Which version is available may be dependent on the machine.

Refer to these links for further details:

* General overview: https://developer.apple.com/opencl/
* Version overview: https://support.apple.com/en-gb/HT202823 (no longer maintained)
* Programming guide: https://developer.apple.com/library/archive/documentation/Performance/Conceptual/OpenCL_MacProgGuide/Introduction/Introduction.html
