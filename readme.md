# CrossWindow

[![cmake-img]][cmake-url]
[![License][license-img]][license-url]
[![Unit Tests][travis-img]][travis-url]
[![Coverage Tests][codecov-img]][codecov-url]

A basic cross platform windowing library for Windows, Mac, Linux, Android, iOS, and WebAssembly.

- Window Creation

- Basic Input

- OS Dialogs

## Usage

First create a main delegate function `xmain` where you'll put your application logic:

```cpp
#include "CrossWindow/CrossWindow.h"

int xmain(int argc, const char** argv)
{
    // Create Window Object
    xwin::WindowDesc windowDesc;
    windowDesc.name = "Test";
    windowDesc.title = "My Title";
    windowDesc.visible = true;
    windowDesc.width = 1280;
    windowDesc.height = 720;

    xwin::Window window;
    if (window.create(windowDesc))
    {
        while (window.eventLoop())
        {
            // Run renderer logic here
        }
    }
}
```

This xmain function will be called from a platform specific main function that can be included in your main project by CMake or manually inserted by copying all files in `/src/Main/`. If you ever need to access something from that main function for whatever reason, you'll find it in `xwin::getXWinState()`.

For more examples visit the [Documentation](/docs).

## Development

Be sure to have [CMake](https://cmake.org) Installed.

| CMake Options | Description |
|:-------------:|:-----------:|
| `BUILD_TESTS` | Whether or not unit tests are enabled. Defaults to `OFF`, Can be `ON` or `OFF`. |
| `OPERATING_SYSTEM ` | What Operating System to build for, defaults to `AUTO`, can be `NOOP`, `WINDOWS`, `MACOS`, `LINUX`, `ANDROID`, `IOS`, `WASM`.  |

We would recommend making a folder where solution files will be built to to avoid making your file system look too messy, such as `visualstudio/` or `xcode/` depending on the platform you're building for. `cd` to that directory and type in your terminal:

```bash
# ⚗️ To build solution with tests
cmake -DBUILD_TESTS=ON ..

# Or...

cmake -G Xcode -DBUILD_TESTS=ON -DOPERATING_SYSTEM=MACOS ..
```

Whenever you add new files to the project, run `cmake ..`, and if you edit the `CMakeLists.txt` file be sure to delete your `CMakeCache.txt` and `CMakeFiles/` and run Cmake again.

## License

CrossWindow is licensed as either **MIT** or **Apache-2.0**, whichever you would prefer.

[cmake-img]: https://img.shields.io/badge/cmake-3.9-1f9948.svg?style=flat-square
[cmake-url]: https://cmake.org/
[license-img]: https://img.shields.io/:license-©-blue.svg?style=flat-square
[license-url]: https://opensource.org/licenses/MIT
[travis-img]: https://img.shields.io/travis/alaingalvan/crosswindow.svg?style=flat-square
[travis-url]: https://travis-ci.org/alaingalvan/crosswindow
[codecov-img]:https://img.shields.io/codecov/c/github/alaingalvan/crosswindow.svg?style=flat-square
[codecov-url]: https://codecov.io/gh/alaingalvan/crosswindow