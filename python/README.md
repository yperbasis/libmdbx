It seems that we should stop these experiment and never mix the build of the library itself with the binding for a runtimes/languages that have their own build/import infrastructure.

The main problem is that with this way we should to use already (reasonable) selected tools (i.e. `GNU make` and `CMake`) to build a bindings.
This lead to a build hell, since instead of using ready-made solutions, we need to re-implement them using GNU Make and CMake, simultaneously integrate with present build features and scenarios.

Therefore, the basic rules for bindings are as follows:

1. Never mix-in a bindings which requires more than GNU Make and CMake using in a traditional way   (actually only C++ bindings are satisfy this).
2. Bindings MUST build _libmdbx_ by the `CMake` scripts which are provide here or should use a pre-builded and installed to a system library (e.g. in a _Buildroot_ case).
3. For bindings are proposed to use the amalgamated source code of _libmdbx_ (i.e. releases snapshots) and optionally be able to use libmdbx as a git submodule.
4. Bindings MUST use a shared variant of _libmdbx_, with exception for embedded platforms without shared libraries support.
5. Bindings MUST must be cross-interoperable each with others, i.e. MUST NOT use build options that lead to incompatibility, and thus an applications written in `Python`, `Rust` and `C++` will be able use a single DB with a single shared instance of _libmdbx_.