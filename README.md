# OpenCL wrapper libraries for Go

<img width="100px" src="logo.png" alt="Logo showing four gophers in the colours of OpenCL logo"/>

This repository is the central entry point for [OpenCL](https://www.khronos.org/opencl/) wrapper libraries for [Go](https://go.dev).
It serves as the central information source, issue tracker, and discussion space.

> This GitHub organization is an open-source project and has no affiliation with Khronos Group.

**The wrappers are not in a state to provide useful functionality and contain potential invalid memory access. The repository is archived and unmaintained.
Please see [Maintenance Notice](https://github.com/opencl-go/opencl-go.github.io/discussions/25) for further details.**

## Motivation

The goal of this project is to maintain OpenCL wrapper libraries that

* Provide the full functionality of main OpenCL API
* Provide documentation to help in the usage of the API
* Handle the most low-level properties of the API to expose a more Go-idiomatic approach
* Allow extensibility via OpenCL extensions
* Are also available for newer API versions (OpenCL 2.2, 3.0)

## Further links

* [Overview on GitHub](https://github.com/opencl-go)
* [Discussions and questions](https://github.com/opencl-go/opencl-go.github.io/discussions)
* [Issue tracker](https://github.com/opencl-go/opencl-go.github.io/issues)
* Versioned OpenCL wrappers:
  * [OpenCL 3.0](https://github.com/opencl-go/cl30)
  * [OpenCL 2.2](https://github.com/opencl-go/cl22)
  * [OpenCL 1.2](https://github.com/opencl-go/cl12)
* Examples
  * [Basic](https://github.com/opencl-go/examples-basic)
* [This page](https://opencl-go.github.io/)

## How-To guides

* [How to install the OpenCL SDK](how-to-install-sdk.md)

## Questions and general information

* [Design principles](faq-design-principles.md)
* [Alternative wrapper libraries](faq-alternatives.md)

## Legal

The wrapper libraries are licensed under the MIT license. See the `LICENSE` files in the respective repository.

The logo of the opencl-go project is based on the original gopher mascot design by Renee French,
licensed under the [Creative Commons Attribution 3.0 Unported](https://creativecommons.org/licenses/by/3.0/deed.en) license. 
