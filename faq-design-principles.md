# Design principles

This page collects answers and guides to "why" some things are as they are in this project.
The details should help to re-evaluate them in the future, should conditions change.

## Allow targeting of different OpenCL versions

It shall be possible to develop against a particular version of the OpenCL API, and also stay compatible
to be integrated with a library or application that targets a different version of the OpenCL API.

Use-case here can be that a library developer implements a particular algorithm using the API surface of
OpenCL 1.2 for maximum portability. And an application that requires OpenCL 3.0 functionality
while making use of that extra library.
The application developer in this case wants to be able to build in version 3.0 and also build that library.

## Why separate repositories per OpenCL version?

Here the user-experience was the primary driving factor. The two main components are:
* Go documentation
* Ease of compilation

As an added point for consideration is the previous one, the demand that they can be combined in a single
application in different versions.

[Alternative wrapper libraries](faq-alternatives.md) typically come in two flavours: those using build tags to separate API level and
those having different sub-folders.
Those with separate folders demand that a user has an SDK that supports all the API levels in order to build the entire project.
This also causes a longer compilation time.

In contrast, when using build tags, then there is only "one" version visible - depending on this tag is selected, and which is the default.
The default tag(s) then also govern which Go documentation is visible, possibly limiting or giving wrong impressions.

Considering deprecated APIs, the library that only needs OpenCL 1.2 is free to work on this API level - despite some
used function or constants are deprecated in future versions.

A further factor is the future extensibility: If a future OpenCL API version is released, how shall the "default" level of one repository be affected?
Should it stay at the level that was used when the project was created, or shall it update?
This then also has consequences on the Go versioning. 

With separate repositories, it is possible to have specific documentation per API level, and compilation is focused on only that level.

This is also in line with Go module versioning: Instead of making it difficult to hide different versions within
one repository (through branches, paths, or tags), create a dedicated repository that lives independently.

## Support extensions from external sources

It shall be possible to implement extensions without the need to extend a repository.

This has implications on the provided API: To stay consistent, all the functions should be available as functions that take
the affected objects as a parameter.

For example, there is `ReleaseContext(Context)` instead of (only) `Context.Release()`.
This is then in line with the `cl_khr_terminate_context` extension: It provides a function `TerminateContext(Context)`.
If that extension is external (a separate repository), it would not be able to add a `Context.Terminate()` function.

> Even if the `cl_khr_terminate_context` extension is part of the repository, the potentially exported `Context.Terminate()`
> function may be misleading if the extension is not available on the system.

As a result, the exposed types, such as `Context` or `CommandQueue` must be usable in a way to expose the underlying
C-API type for external functions to work.

This also supports in the compatibility between the different version repositories: Through a cast, a type
can be converted from a 1.2 domain to a 3.0 domain and the other way back.

## OpenCL 1.2 is the baseline

At the time of creation of this project, OpenCL 3.0 was already released. As part of this release, version 1.2
has been declared as the mandatory baseline for functionality.

This project follows this decision to ignore versions 1.0 and 1.1.

## The exported API shall be documented

In contrast to all the other wrappers, have a library that provides helpful documentation.

However, it is not necessary to copy the entire official Khronos OpenCL documentation.
Instead, have all the APIs refer to the full documentation, and provide an abstract of the general behaviour.
This documentation shall also take into account any Go-specific wrapping that took place.

Refer to the Creative Commons licensed asciidoctor files from https://github.com/KhronosGroup/OpenCL-Docs when creating the abstract.

## Side effects and consequences

Because of the taken decisions, the following side effects and consequences are the result:

* C-helper functions must all be prefixed with the version of the repository they are for.
  Otherwise, the linker would fail in case a project combines multiple projects.
  This prefix can be seen as the C-equivalent of the Go package.
* Deprecated APIs must be available by default. In case a library or application wants to upgrade to a higher
  version, it should still compile, and ideally provide "deprecation" messages where suitable.
  With OpenCL 1.2 being the baseline, versions 1.0 and 1.1 are ignored.
