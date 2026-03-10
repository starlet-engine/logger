# Starlet Logger

![Tests](https://github.com/starlet-engine/logger/actions/workflows/test.yml/badge.svg)
[![C++17](https://img.shields.io/badge/C%2B%2B-17-blue.svg)](https://isocpp.org/std/the-standard)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

A lightweight logging utility for C++ applications.

## Features
- Four log levels: Info, Debug, Warning, Error
- Automatic stream routing (stdout for info/debug, stderr for warnings/errors)
- Caller, function, and msg context in every log message
- Debug logs compiled out in release builds (NDEBUG)
- Custom warning return value for permissible warnings

## Prerequisites
- C++17 or later
- One of the following Build Systems,
    - CMake 3.20+
    - Meson 1.1+

## Using as a Dependency

### CMake
```cmake
include(FetchContent)

FetchContent_Declare(starlet_logger
  GIT_REPOSITORY https://github.com/starlet-engine/logger.git 
  GIT_TAG main
)
FetchContent_MakeAvailable(starlet_logger)

target_link_libraries(app_name PRIVATE starlet_logger)
```

### Meson
> **Note:** Meson does not fetch dependencies automatically. Add the [`starlet_logger.wrap`](./subprojects/starlet_logger.wrap) file to your project's `subprojects` directory.

In your `meson.build`:

```python
starlet_logger = subproject('starlet_logger')
starlet_logger_dep = starlet_logger.get_variable('starlet_logger_dep')
executable('app_name', 'main.cpp', dependencies: starlet_logger_dep)
```

## Building and Testing
```bash
# 1. Clone starlet-logger
git clone https://github.com/starlet-engine/logger.git
cd starlet-logger
```

### CMake
```bash
cmake -B build -DBUILD_TESTS=ON
cmake --build build
ctest --test-dir build
```

### Meson
```bash
meson setup build -Dbuild_tests=true
meson compile -C build
meson test -C build
```

## License
MIT License - see [LICENSE](./LICENSE) for details.
