Based on [this](https://docs.conan.io/en/latest/getting_started.html) doc.


System configuration:

```bash
mkdir -p ~/.conan/profiles/
echo compiler.libcxx=libstdc++11 >> ~/.conan/profiles/default
```

```bash
# If you don't want to do the above, here is an optional config for backward compatibility ABI setting
conan profile new default --detect
conan profile update settings.compiler.libcxx=libstdc++11 default
```

```bash
mkdir -p build
cd build/
# Installs the prereqs & toolchains to complete build process
conan install .. --build missing
cmake ..
make
```
