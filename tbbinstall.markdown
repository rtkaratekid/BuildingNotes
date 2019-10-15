### Install intel TBB library
#### Worked for Ubuntu 18.04

```
git clone https://github.com/wjakob/tbb.git
cd tbb/build
cmake ..
make -j
sudo make install
```

### Example valid cpp file now

```cpp
#include <tbb/task.h>

int main() {
    return 0;
}
```
