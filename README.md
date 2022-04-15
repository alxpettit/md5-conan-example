Based on [this](https://docs.conan.io/en/latest/getting_started.html) doc.

```bash
# $ conan profile new default --detect  # Generates default profile detecting GCC and sets old ABI
# $ conan profile update settings.compiler.libcxx=libstdc++11 default  # Sets libcxx to C++11 ABI
mkdir -p build
cd build/
# Installs the prereqs & toolchains to complete build process
conan install .. --build missing
cmake ..
make
```
