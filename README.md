# Build 

## Build Linux

### **1.1 Install dependent libraries**

* For loading caffe model or tensorflow model
``` 
    sudo apt install libprotobuf-dev protobuf-compiler
```

* if use the fedora/Centos ,use follow command instead.
```
    sudo dnf install protobuf-devel
    sudo dnf install boost-devel glog-devel
```
* install pkg-config
```
sudo apt install pkg-config
```
### **1.2 Prepare config files**
* Edit `./tengine-module/default.config`

    * set tengine root path, protobuf include / lib path
        ```
        TENGINE_ROOT=/home/test/tengine                                                 // tengine root path

        PROTOBUF_INCLUDE_PATH=/home/test/protobuf/android-ndk-r16/Android-22/include/

        PROTOBUF_LIB_PATH=/home/test/protobuf/android-ndk-r16/Android-22/arm64_lib/
        ```
    if want to run Tengine with ACL, please set the correct ACL_ROOT path

### **1.3 Build**
```
cd ~/tengine/tengine-module
mkdir build
cd build
../linux_build.sh
make -j4
```

## Build Android

### **1.1 Download Android ndk,Protobuf and ComputeLibrary

Download the below files from [Tengine Android build](https://pan.baidu.com/s/1-zsqxXXcZEXmCip-nQzcIw) (password: *wtcz*):
```
  - android-ndk-r16-linux-x86_64.zip
  - protobuf_lib.tgz
  - ComputeLibrary.tgz
```
### **1.2 Unpack Android ndk, OpenBLAS, Protobuf and ComputeLibrary
```
unzip android-ndk-r16-linux-x86_64.zip
tar -zxvf protobuf_lib.tgz
tar -zxvf ComputeLibrary.tgz
```
### **1.4 Prepare config files**
* Edit `./tengine-module/default.config`

    * set tengine root path, protobuf include / lib path
        ```
        TENGINE_ROOT=/home/test/tengine                                                 // tengine root path

        ARCH_TYPE="Arm64"

        ANDROID_NDK=/home/test/android-ndk-r16

        API_LEVEL=22

        PROTOBUF_INCLUDE_PATH=/home/test/protobuf/android-ndk-r16/Android-22/include/

        PROTOBUF_LIB_PATH=/home/test/protobuf/android-ndk-r16/Android-22/arm64_lib/
        ```
    if want to run Tengine with ACL, please set the correct ACL_ROOT path
### **1.5 Build**
```
cd ~/tengine/tengine-module
mkdir build
cd build
../android_build.sh
make -j4
```
