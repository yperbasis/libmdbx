Incomplete TODO list to merge `python-bindings` (status: draft) branch to the `master` (status: ready for use):

0.

 - [ ] Q: does the `python/libmdbx/` subdirectory is required instead of just `python/` ?
 - [ ] Q: does names like  `MDBXFoo` is reasonable instead of using namespace(s) or `MDBX_Foo` ?
 - [ ] Q: could we use some automation to update, synchronize and/or check definitions and doxygen-comments ?

1.

 - [x] cmake: enable python binding only for cmake >= 3.14 and warn otherwise (but we unable change the requirement for minimal cmake version).
 - [x] cmake: use `FindPython()` instead of calling `python` directly.
 - [x] cmake: always use `python3 -m pytest` instead of finding `pytest`, since such way is fragile and unportable.
 - [x] cmake: replace using `sed` by CMake's `configure_file()`.
 - [ ] cmake: seems CMake have some useful features for python than we should use instead of custom targets.
 - [ ] python: no build-depend files should be created inside `${CMAKE_CURRENT_SOURCE_DIR}`, but only `${CMAKE_CURRENT_BINARY_DIR}` instead.
 - [ ] python: should should refer to the installed libmdbx.so, but not to a build's temporary artifact(s).
 - [ ] python: A different package name must be chosen, otherwise there is confusion with the generally accepted names of source code archives (and someone should be reserved for full C++ bindings by pybind11).
 - [ ] create README.md
 - [ ] egg/wheel: ability to build & install library from pip.

2.

 - [ ] integration: provide & fix building from both amalgamated and non-amalgamated sources.
 - [ ] integration: manually check & fix all building variants with all libmdbx cases (static, solib/dll, windows-without-crt, with/without LTO).
 - [ ] integration: manually check & fix building by: clang 4.0..latest, gcc 4.8..latest.
 - [ ] ci: provide scripts for checking builds on Windows and FreeBSD.
 - [ ] integration: manually check & fix for Buildroot (i.e. cross-compilation) with all python-related options.
 - [ ] integration: manually check & fix for Solaris/OpenIndiana, OpenBSD, NetBSD, DragonflyBSD, Android, iOS.

3.

 - [ ] code: fix a hardcoded platform-depended error codes (MDBX_ENODATA, MDBX_EINVAL, MDBX_EACCESS, MDBX_ENOMEM, MDBX_EROFS, MDBX_ENOSYS, MDBX_EIO, MDBX_EPERM, MDBX_EINTR, MDBX_ENOFILE, MDBX_EREMOTE, etc ?).
 - [ ] feedback: take into account the wishes and recommendations of users.
 - [ ] coverity: check bindings with CoverityScan.
 - [ ] ci: add checking within CentOS 6.x .. latest (this is also applicable for mainstream).