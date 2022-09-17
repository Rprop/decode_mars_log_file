[![Build status](https://github.com/RProp/decode_mars_log_file/actions/workflows/build.yml/badge.svg)](https://github.com/RProp/decode_mars_log_file/actions/workflows/build.yml)
![GitHub contributors](https://img.shields.io/github/contributors/RProp/decode_mars_log_file)
![GitHub all releases](https://img.shields.io/github/downloads/RProp/decode_mars_log_file/total)
![GitHub release (latest by SemVer)](https://img.shields.io/github/downloads/RProp/decode_mars_log_file/latest/total)
![Latest release](https://img.shields.io/github/release/RProp/decode_mars_log_file.svg)

1. 修改 decode_log_file.c 中的 PRIV_KEY 和 PUB_KEY
2. 使用 cmake 编译

## Download Pre-Built Binaries
- latest [unstable build ![GitHub commits since tagged version (branch)](https://img.shields.io/github/commits-since/RProp/decode_mars_log_file/latest/main)](https://nightly.link/RProp/decode_mars_log_file/workflows/build/main)


## Format
```
clang-format -i --sort-includes ./decode_log_file.c
```

## Build for Windows
```
cmake -G "Visual Studio 17 2022" -A x64 -T host=x64 -S ./ -B ./build_win
```

## Build for Android
```
%path_to_cmake%/bin/cmake ^
-DANDROID_ABI=arm64-v8a ^
-DANDROID_PLATFORM=android-30 ^
-DANDROID_NDK=%path_to_ndk% ^
-DCMAKE_TOOLCHAIN_FILE=%path_to_ndk%/build/cmake/android.toolchain.cmake ^
-DCMAKE_GENERATOR=Ninja ^
-DCMAKE_MAKE_PROGRAM=%path_to_cmake%/bin/ninja ^
-S ./ ^
-B ./build_android
```
```
cd ./build_android
%path_to_cmake%/bin/ninja
```
