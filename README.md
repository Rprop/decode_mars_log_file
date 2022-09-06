1. 修改 decode_log_file.c 中的 PRIV_KEY 和 PUB_KEY
2. 使用 cmake 编译
服务器上没装 cmake 的话，用 gcc 编译：

```
gcc decode_log_file.c micro-ecc-master/uECC.c -o decode_log_file -O0 -ggdb -lz
```

## Format
```
clang-format.exe -i --sort-includes ./decode_log_file.c
```

## Build for Windows
```
cmake.exe ^
-S ./ ^
-B ./build ^
-G "Visual Studio 17 2022" ^
-A x64 ^
-T host=x64
```

## Build for Android
```
cmake.exe ^
-DANDROID_ABI=arm64-v8a ^
-DANDROID_NDK=%path_to_ndk% ^
-DANDROID_PLATFORM=android-30 ^
-DCMAKE_TOOLCHAIN_FILE=%path_to_ndk%\build\cmake\android.toolchain.cmake ^
-DCMAKE_GENERATOR=Ninja ^
-DCMAKE_MAKE_PROGRAM=%path_to_cmake%\bin\ninja.exe ^
-S ./ ^
-B ./build_android
```
```
cd ./build_android
%path_to_cmake%\bin\ninja.exe
```
