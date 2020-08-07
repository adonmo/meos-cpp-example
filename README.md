# MEOS C++ example

This project shows a minimal example for how [MEOS](https://github.com/adonmo/meos) can be used in C++ projects.

## Code Snippet

```cpp
#include <iostream>
#include <meos/types/temporal/TSequence.hpp>
#include "time_utils.cpp"

using namespace std;
using namespace meos;


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
cmake -B build -S .
cmake --build build
```

Note: It is assumed you have libgeos-dev installed on your system.

## Running

```sh
./build/app
```
If you see the following output, you have succesfully ran the example application! :)
```
[2@2012-01-01T00:00:00+0000, 1@2012-01-02T00:00:00+0000, 4@2012-01-03T00:00:00+0000, 3@2012-01-04T00:00:00+0000)
```

## How it works

In [CMakeLists.txt](CMakeLists.txt) file you can see that MEOS is included and linked using [CPM](https://github.com/TheLartians/CPM.cmake)

```cmake
include(cmake/CPM.cmake)

CPMAddPackage(
  NAME MEOS
  GITHUB_REPOSITORY adonmo/meos
  GIT_TAG 0.1
)
```

When you run cmake build, specified version of the library is fetched and linked to the application

## Ready for more?
Of course, you can build much more useful and all sorts of complex applications using MEOS. Here are some links to help you out:

  - [MEOS C++ Documentation](https://adonmo.github.io/meos/)
  - [MEOS Repository](https://github.com/adonmo/meos)
  - [MobilityDB](https://github.com/MobilityDB/MobilityDB) and its [documentation](https://docs.mobilitydb.com/MobilityDB/master/)
