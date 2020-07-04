# MEOS C++ example

This project shows a minimal example for how MEOS can be used in C++ projects.

## Code Snippet

```cpp
#include <iostream>
#include <meos/types/temporal/TSequence.hpp>
#include "time_utils.cpp"
using namespace std;


int main() {
    set<TInstant<int>> instants = {
        TInstant<int>(2, unix_time_point(2012, 1, 1)),
        TInstant<int>(1, unix_time_point(2012, 1, 2)),
        TInstant<int>(4, unix_time_point(2012, 1, 3)),
        TInstant<int>(3, unix_time_point(2012, 1, 4)),
    };
    TSequence<int> tseq(instants);
    cout << tseq << endl;
    return 0;
}
```

## Building

```sh
$ cmake -B build -S .
$ cmake --build build
```

Note: It is assumed you have libgeos-dev installed on your system.

## Running

```sh
$ ./build/app
[2@2012-01-01T00:00:00+0000, 1@2012-01-02T00:00:00+0000, 4@2012-01-03T00:00:00+0000, 3@2012-01-04T00:00:00+0000)
```

## How it works

In CMakeLists.txt file you can see that MEOS is included and linked using CPM

```cmake
include(cmake/CPM.cmake)

CPMAddPackage(
  NAME MEOS
  GITHUB_REPOSITORY chaitan94/meos
  GIT_TAG f1f7699e1e3a1a941cdebdaf881c2003a5ed32e0
)
```

When you run cmake build, specified version of the library is fetched and linked to the application
