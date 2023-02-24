---
title : Conan
date : 2023-02-24_Fri 13:41
aliases : [c++, conan, package manager]
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[]]<br>
Parent Link :: [[]]<br>

---
# Conan Introduction
> Conan, software package manager for C and C++ developers.<br>
> The open source, decentralized and multi-platform package manager to create and share all your native binaries.

## Example

### files
* files structure
```
project/
├─── build/
├─┬─ src/
│ └─── hello.cpp
├─── CMakeLists.txt
├─── conanfile.txt
└─── README
```

* hello.cpp
```cpp
#include "Poco/Thread.h"
#include "Poco/Runnable.h"
#include <iostream>

class HelloRunnable: public Poco::Runnable {

    virtual void run() {

        std::cout << "Hello, world!" << std::endl;
    }
};

int main() {

    HelloRunnable runnable;
    Poco::Thread thread;
    thread.start(runnable);
    thread.join();
    return 0;
}
```

* CMakeLists.txt
```cmake
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
PROJECT(HELLOLIB)
ADD_EXECUTABLE(hello src/hello.cpp)
```

* conanfile.txt
```conan
[requires]
Poco/1.9.4@pocoproject/stable

[generators]
cmake
```
用 `conan search` 來找 packages，`@` 後面的不是必要的

### install conan
```bash
$ cd build
$ conan install ..
```
<br>

目錄會變成
```
project/
├─┬─ build/
│ ├─── ...
│ ├─── conanbuildinfo.cmake
│ └─── ...
├─┬─ src/
│ ├─── CMakeLists.txt
│ └─── hello.cpp
├─── CMakeLists.txt
├─── conanfile.txt
└─── README
```

### modify CMakeLists.txt
```cmake
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
PROJECT(HELLOLIB)

INCLUDE(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
CONAN_BASIC_SETUP()

INCLUDE_DIRECTORIES(${CONAN_INCLUDE_DIRS})
MESSAGE(STATUS ${CONAN_INCLUDE_DIRS})

ADD_EXECUTABLE(hello src/hello.cpp)  
TARGET_LINK_LIBRARIES(hello ${CONAN_LIBS})
```

### use cmake to build
```bash
$ cmake ..
$ cmake --build .

$ ./bin/hello
> Hello, world!
```