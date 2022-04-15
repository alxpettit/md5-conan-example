Based on [this](https://docs.conan.io/en/latest/getting_started.html) doc.

# backward compatibility ABI setting
(see [here](https://docs.conan.io/en/latest/howtos/manage_gcc_abi.html#manage-gcc-abi))
```bash
mkdir -p ~/.conan/profiles/
vim ~/.conan/profiles/default
```

Then, under `ini`, make sure your settings are as such:
```ini
[settings]
.   .   .
compiler.libcxx=libstdc++11
```

```bash
# If you don't want to do the above, here is another way
conan profile new default --detect
conan profile update settings.compiler.libcxx=libstdc++11 default
```

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
