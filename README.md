## Laboratory work V

## Homework

### Задание

1. Создайте `CMakeList.txt` для библиотеки *banking*. 

**banking/CMakeLists.txt**:

```
cmake_minimum_required(VERSION 3.16.3)

set(CMAKE_TRY_COMPILE_TARGET_TYPE "STATIC_LIBRARY")

project(banking)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(banking STATIC Account.cpp Account.h Transaction.cpp Transaction.h)
```

**CMakeLists.txt**:

```
cmake_minimum_required(VERSION 3.4)

SET(COVERAGE OFF CACHE BOOL "Coverage")
SET(CMAKE_CXX_COMPILER "/usr/bin/g++")

project(TestRunning)

add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/gtest" "gtest")

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/banking)

add_executable(RunTest ${CMAKE_CURRENT_SOURCE_DIR}/test.cpp)

if (COVERAGE)
    target_compile_options(RunTest PRIVATE --coverage)
    target_link_libraries(RunTest PRIVATE --coverage)
endif()

target_include_directories(RunTest PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/banking)

target_link_libraries(RunTest PRIVATE gtest gtest_main gmock_main banking)
```

2. Создайте модульные тесты на классы `Transaction` и `Account`.
    
3. Настройте сборочную процедуру на **TravisCI**.
4. Настройте [Coveralls.io](https://coveralls.io/).

