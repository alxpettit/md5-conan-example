Based on [this](https://docs.conan.io/en/latest/getting_started.html) doc.

# Prereqs for toolchain

- make
- cmake
- conan
- gcc/clang prolly I dunno, fuck off

# Getting repo

```bash
git clone "https://github.com/alxpettit/md5-conan-example"
cd md5-conan-example/
```

# backward compatibility ABI setting

In a nutshell, the Conan is boomer and defaults to configuring a boomer [ABI](https://en.wikipedia.org/wiki/Application_binary_interface) for backward compatibility. In practice, this breaks anything using a version of C++ newer than 2011, due to COW strings and whatever the fuck else.

You might say, 'but Alexandria, 2011 was over a decade ago!'

*YES.* ***I KNOW.*** Welcome to C++ programming, fucker.

(see the official docs for this issue here [here](https://docs.conan.io/en/latest/howtos/manage_gcc_abi.html#manage-gcc-abi))

Anyway, here's the workaround:

```bash
conan profile new default --detect
conan profile update settings.compiler.libcxx=libstdc++11 default
```

Under `~/.conan/profiles/default`, this sets the following:
```ini
[settings]
.   .   .
compiler.libcxx=libstdc++11
```

# Prereqs & actually building your thing

```bash
# We prefer to build in build directory to keep build artifacts separate from source code
mkdir -p build
cd build/
# Installs the prereqs & toolchains to complete build process
conan install .. --build missing
# From here, conventional cmake/make toolchain techniques apply
cmake ..
make
```
