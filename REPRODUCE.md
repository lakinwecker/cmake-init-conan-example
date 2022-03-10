# Reproducing my issue

## Works
```sh
rm -rf conan build
conan install . -if conan -s build_type=Debug
cmake --preset=dev
VERBOSE=1 cmake --build --preset=dev
```

## Doesn't work
```sh
rm -rf conan build
conan install . -if conan
cmake --preset=dev
VERBOSE=1 cmake --build --preset=dev
```

### output
```sh
cmake-init-conan-example on  master [⇡?] is 📦 v0.1.0 via 🐍 v3.10.2 (.venv)
➜ rm -rf conan build

cmake-init-conan-example on  master [⇡?] is 📦 v0.1.0 via 🐍 v3.10.2 (.venv)
➜ conan install . -if conan
Configuration:
[settings]
arch=x86_64
arch_build=x86_64
build_type=Release
compiler=gcc
compiler.libcxx=libstdc++
compiler.version=11
os=Linux
os_build=Linux
[options]
[build_requires]
[env]

conanfile.txt: Installing package
Requirements
    doctest/2.4.6 from 'conancenter' - Cache
    eigen/3.3.9 from 'conancenter' - Cache
    imgui/1.81 from 'conancenter' - Cache
Packages
    doctest/2.4.6:5ab84d6acfe1f23c4fae0ab88f26e3a396351ac9 - Cache
    eigen/3.3.9:5ab84d6acfe1f23c4fae0ab88f26e3a396351ac9 - Cache
    imgui/1.81:d8d8aba822aaa76849d2f1bafe4a2a62a9f83b74 - Cache

Installing (downloading, building) binaries...
doctest/2.4.6: Already installed!
eigen/3.3.9: Already installed!
imgui/1.81: Already installed!
imgui/1.81: Appending PATH env var with : /home/lakin/.conan/data/imgui/1.81/_/_/package/d8d8aba822aaa76849d2f1bafe4a2a62a9f83b74/bin
conanfile.txt: Generator cmake_find_package_multi created imgui-config-version.cmake
conanfile.txt: Generator cmake_find_package_multi created imgui-config.cmake
conanfile.txt: Generator cmake_find_package_multi created imguiTargets.cmake
conanfile.txt: Generator cmake_find_package_multi created imguiTarget-release.cmake
conanfile.txt: Generator cmake_find_package_multi created Eigen3ConfigVersion.cmake
conanfile.txt: Generator cmake_find_package_multi created Eigen3Target-release.cmake
conanfile.txt: Generator cmake_find_package_multi created Eigen3Targets.cmake
conanfile.txt: Generator cmake_find_package_multi created Eigen3Config.cmake
conanfile.txt: Generator cmake_find_package_multi created doctest-config-version.cmake
conanfile.txt: Generator cmake_find_package_multi created doctest-config.cmake
conanfile.txt: Generator cmake_find_package_multi created doctestTargets.cmake
conanfile.txt: Generator cmake_find_package_multi created doctestTarget-release.cmake
conanfile.txt: Generator txt created conanbuildinfo.txt
conanfile.txt: Aggregating env generators
conanfile.txt: Generated conaninfo.txt
conanfile.txt: Generated graphinfo

cmake-init-conan-example on  master [⇡?] is 📦 v0.1.0 via 🐍 v3.10.2 (.venv)
➜ cmake --preset=dev
Preset CMake variables:

  CMAKE_BUILD_TYPE="Debug"
  CMAKE_CXX_EXTENSIONS="OFF"
  CMAKE_CXX_FLAGS="-Wall -Wextra -Wpedantic -Wconversion -Wsign-conversion -Wcast-qual -Wshadow -Wformat=2 -Wundef -Werror=float-equal"
  CMAKE_CXX_STANDARD="17"
  CMAKE_CXX_STANDARD_REQUIRED="ON"
  CMAKE_EXPORT_COMPILE_COMMANDS="True"
  CMAKE_MODULE_PATH="/home/lakin/school-repos/cmake-init-conan-example/conan/"
  CMAKE_PREFIX_PATH="/home/lakin/school-repos/cmake-init-conan-example/conan/"
  conan-example_DEVELOPER_MODE="ON"

-- The CXX compiler identification is GNU 11.2.0
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Library imgui found /home/lakin/.conan/data/imgui/1.81/_/_/package/d8d8aba822aaa76849d2f1bafe4a2a62a9f83b74/lib/libimgui.a
-- Found: /home/lakin/.conan/data/imgui/1.81/_/_/package/d8d8aba822aaa76849d2f1bafe4a2a62a9f83b74/lib/libimgui.a
-- Configuring done
-- Generating done
-- Build files have been written to: /home/lakin/school-repos/cmake-init-conan-example/build/dev

cmake-init-conan-example on  master [⇡?] is 📦 v0.1.0 via 🐍 v3.10.2 (.venv)
➜ VERBOSE=1 cmake --build --preset=dev
/usr/bin/cmake -S/home/lakin/school-repos/cmake-init-conan-example -B/home/lakin/school-repos/cmake-init-conan-example/build/dev --check-build-system CMakeFiles/Makefile.cmake 0
/usr/bin/cmake -E cmake_progress_start /home/lakin/school-repos/cmake-init-conan-example/build/dev/CMakeFiles /home/lakin/school-repos/cmake-init-conan-example/build/dev//CMakeFiles/progress.marks
/usr/bin/make  -f CMakeFiles/Makefile2 all
make[1]: Entering directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
/usr/bin/make  -f CMakeFiles/conan-example_exe.dir/build.make CMakeFiles/conan-example_exe.dir/depend
/usr/bin/make  -f test/CMakeFiles/conan-example_test.dir/build.make test/CMakeFiles/conan-example_test.dir/depend
make[2]: Entering directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
cd /home/lakin/school-repos/cmake-init-conan-example/build/dev && /usr/bin/cmake -E cmake_depends "Unix Makefiles" /home/lakin/school-repos/cmake-init-conan-example /home/lakin/school-repos/cmake-init-conan-example /home/lakin/school-repos/cmake-init-conan-example/build/dev /home/lakin/school-repos/cmake-init-conan-example/build/dev /home/lakin/school-repos/cmake-init-conan-example/build/dev/CMakeFiles/conan-example_exe.dir/DependInfo.cmake --color=
make[2]: Entering directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
cd /home/lakin/school-repos/cmake-init-conan-example/build/dev && /usr/bin/cmake -E cmake_depends "Unix Makefiles" /home/lakin/school-repos/cmake-init-conan-example /home/lakin/school-repos/cmake-init-conan-example/test /home/lakin/school-repos/cmake-init-conan-example/build/dev /home/lakin/school-repos/cmake-init-conan-example/build/dev/test /home/lakin/school-repos/cmake-init-conan-example/build/dev/test/CMakeFiles/conan-example_test.dir/DependInfo.cmake --color=
make[2]: Leaving directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
make[2]: Leaving directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
/usr/bin/make  -f CMakeFiles/conan-example_exe.dir/build.make CMakeFiles/conan-example_exe.dir/build
/usr/bin/make  -f test/CMakeFiles/conan-example_test.dir/build.make test/CMakeFiles/conan-example_test.dir/build
make[2]: Entering directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
make[2]: Entering directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
[ 50%] Building CXX object test/CMakeFiles/conan-example_test.dir/source/conan-example_test.cpp.o
[ 50%] Building CXX object CMakeFiles/conan-example_exe.dir/source/main.cpp.o
/usr/bin/c++   -Wall -Wextra -Wpedantic -Wconversion -Wsign-conversion -Wcast-qual -Wshadow -Wformat=2 -Wundef -Werror=float-equal -g -std=c++17 -MD -MT CMakeFiles/conan-example_exe.dir/source/main.cpp.o -MF CMakeFiles/conan-example_exe.dir/source/main.cpp.o.d -o CMakeFiles/conan-example_exe.dir/source/main.cpp.o -c /home/lakin/school-repos/cmake-init-conan-example/source/main.cpp
cd /home/lakin/school-repos/cmake-init-conan-example/build/dev/test && /usr/bin/c++  -DDOCTEST_CONFIG_IMPLEMENT_WITH_MAIN  -Wall -Wextra -Wpedantic -Wconversion -Wsign-conversion -Wcast-qual -Wshadow -Wformat=2 -Wundef -Werror=float-equal -g -std=c++17 -MD -MT test/CMakeFiles/conan-example_test.dir/source/conan-example_test.cpp.o -MF CMakeFiles/conan-example_test.dir/source/conan-example_test.cpp.o.d -o CMakeFiles/conan-example_test.dir/source/conan-example_test.cpp.o -c /home/lakin/school-repos/cmake-init-conan-example/test/source/conan-example_test.cpp
/home/lakin/school-repos/cmake-init-conan-example/test/source/conan-example_test.cpp:1:10: fatal error: doctest/doctest.h: No such file or directory
    1 | #include <doctest/doctest.h>
      |          ^~~~~~~~~~~~~~~~~~~
compilation terminated.
make[2]: *** [test/CMakeFiles/conan-example_test.dir/build.make:76: test/CMakeFiles/conan-example_test.dir/source/conan-example_test.cpp.o] Error 1
make[2]: Leaving directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
make[1]: *** [CMakeFiles/Makefile2:882: test/CMakeFiles/conan-example_test.dir/all] Error 2
make[1]: *** Waiting for unfinished jobs....
/home/lakin/school-repos/cmake-init-conan-example/source/main.cpp:4:10: fatal error: imgui.h: No such file or directory
    4 | #include "imgui.h"
      |          ^~~~~~~~~
compilation terminated.
make[2]: *** [CMakeFiles/conan-example_exe.dir/build.make:76: CMakeFiles/conan-example_exe.dir/source/main.cpp.o] Error 1
make[2]: Leaving directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
make[1]: *** [CMakeFiles/Makefile2:128: CMakeFiles/conan-example_exe.dir/all] Error 2
make[1]: Leaving directory '/home/lakin/school-repos/cmake-init-conan-example/build/dev'
make: *** [Makefile:166: all] Error 2
```
