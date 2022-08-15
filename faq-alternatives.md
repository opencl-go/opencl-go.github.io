# Alternatives to opencl-go

This page collects alternatives to the provided wrappers of [opencl-go](https://github.com/opencl-go).

Listed properties may become out-of date, so double-check with the linked projects about their current state.

> As a general observation, unless otherwise noted, the found projects appeared in an incomplete state and apparently abandoned.

## samuel/go-opencl

* URL: [https://github.com/samuel/go-opencl](https://github.com/samuel/go-opencl)
* Last check of properties: 2022-08
* Last update of project: 2017-11
* Supported OpenCL version(s): 1.1 and 1.2 (one repository, build tags)

This repository comes up high in search results. With over 60 forks and 140 stars, it seems to be a common go-to repository.

Object-details such as properties during creation or info-query are not supported. Several TODO marker in the source base.

> This page will ignore most of the forks, unless they have a particular new property.


## microo8/blackcl

* URL: [https://gitlab.com/microo8/blackcl](https://gitlab.com/microo8/blackcl)
* Last check of properties: 2022-08
* Last update of project: 2019-02
* Supported OpenCL version(s): ?

Originally on [GitHub](https://github.com/microo8/blackcl) and derived from samuel/go-opencl, this is a project with "highly opinionated OpenCL bindings for Go with some black magic".

This project is a more high-level wrapper as it hides some of OpenCL's concepts (such as Platform, Context, or Queue), to provide a more simplified approach.

## MasterOfBinary/go-opencl

* URL: [https://github.com/MasterOfBinary/go-opencl](https://github.com/MasterOfBinary/go-opencl)
* Last check of properties: 2022-08
* Last update of project: 2016-12
* Supported OpenCL version(s): 2.0

Event waitList / return objects are not supported for `Enqueue*` calls;
`EnqueueNDRangeKernel()` does not support specification of global offsets or local work sizes.

## rainliu/gocl

* URL: [https://github.com/rainliu/gocl](https://github.com/rainliu/gocl)
* Last check of properties: 2022-08
* Last update of project: 2016-09
* Supported OpenCL version(s): 1.1, 1.2, 2.0 (one repository, build tags)

On one hand a low-level wrapper that matches closely the C-API, yet also performs parameter checks on its own.
As such, extensions may not be supported.

TODO marker in the source as some features are not implemented, for example pipes.

It contains several examples and demo applications.

## Patagonicus/opencl

* URL: [https://github.com/Patagonicus/opencl](https://github.com/Patagonicus/opencl)
* Last check of properties: 2022-08
* Last update of project: 2017-03
* Supported OpenCL version(s): 1.2

A low-level wrapper. The readme shows a list of intended functions, which is about half finished.

## go-gl/cl

* URL: [https://github.com/go-gl/cl](https://github.com/go-gl/cl)
* Last check of properties: 2022-08
* Last update of project: 2016-04
* Supported OpenCL version(s): 1.0, 1.1, 1.2 (one repository, different sub-packages)

This wrapper seems to be based on some auto-generated code that directly forwards pointers to the Go-API.
