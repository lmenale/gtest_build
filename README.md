# Building GTest & GMock from source

Compiling GTest from source is actually not that difficult.
Here's what you should do:

## 1. Install all the prerequisite libraries (including Bazel)

```sh
sudo apt-get install pkg-config zip g++ zlib1g-dev unzip python openjdk-8-jdk bazel
```

## 2. Build from the package source with CMake.

Keep in mind that GTest installations are easy using cmake to fit your system:

```sh
git clone https://github.com/lmenale/gtest_build.git
cd gtest_build/googletest
mkdir build
cd build
cmake ..
make
cmake .. -DBUILD_SHARED_LIBS=ON
make
sudo cp lib/libgtest* /usr/lib/
sudo ln -s /usr/lib/libgtest.a /usr/local/lib/googletest/libgtest.a
sudo ln -s /usr/lib/libgtest.so /usr/local/lib/googletest/libgtest.so
sudo ln -s /usr/lib/libgtest_main.a /usr/local/lib/googletest/libgtest_main.a
sudo ln -s /usr/lib/libgtest_main.so /usr/local/lib/googletest/libgtest_main.so
sudo cp lib/libgmock* /usr/lib/
sudo ln -s /usr/lib/libgmock.a /usr/local/lib/googletest/libgmock.a
sudo ln -s /usr/lib/libgmock.so /usr/local/lib/googletest/libgmock.so
sudo ln -s /usr/lib/libgmock_main.a /usr/local/lib/googletest/libgmock_main.a
sudo ln -s /usr/lib/libgmock_main.so /usr/local/lib/googletest/libgmock_main.so
cd ..
sudo rm -rf build
```

## 3. Build from the package source with Bazel.

Keep in mind that GTest build with Bazel is very easy step:

```sh
git clone https://github.com/lmenale/gtest_build.git
cd gtest_build/googletest
bazel build //...
sudo cp bazel-bin/libgtest.a /usr/lib/
sudo cp bazel-bin/libgtest.so /usr/lib/
sudo cp bazel-bin/libgtest_main.a /usr/lib/
sudo cp bazel-bin/libgtest_main.so /usr/lib/
sudo ln -s /usr/lib/libgtest.a /usr/local/lib/googletest/libgtest.a
sudo ln -s /usr/lib/libgtest.so /usr/local/lib/googletest/libgtest.so
sudo ln -s /usr/lib/libgtest_main.a /usr/local/lib/googletest/libgtest_main.a
sudo ln -s /usr/lib/libgtest_main.so /usr/local/lib/googletest/libgtest_main.so
cd ..
```

## 4. Install from the package is more easy.

Keep in mind that GTest installations are easy with the package `libgtest-dev` to fit your system:

```sh
sudo apt-get install libgtest-dev
cd /usr/src/googletest
sudo mkdir build
cd build
sudo cmake ..
sudo cmake .. -DBUILD_SHARED_LIBS=ON
sudo make
sudo cp googlemock/gtest/libgtest* /usr/lib/
sudo cp googlemock/libgmock* /usr/lib/
sudo ln -s /usr/lib/libgtest.a /usr/local/lib/googletest/libgtest.a
sudo ln -s /usr/lib/libgtest_main.a /usr/local/lib/googletest/libgtest_main.a
cd ..
sudo rm -rf build
```
