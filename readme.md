
Go into an empty folder and run the following script:

```bash
git clone --recursive https://github.com/malytomas/http-tests.git
cd http-tests/http-tests
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=DEBUG ..
cmake --build . --target http-clienttest -- -j5
bin/http-clienttest
```


