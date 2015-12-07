# OpenCV Face Detection 

This project illustrates OpenCV Face Detection sample in Android Studio.

## Prerequisite:

1. Download and extract OpenCV 3.0 for Android from http://opencv.org/.
2. Download and setup Android NDK build tools: http://developer.android.com/ndk/guides/setup.html
3. Create a new project in Android Studio with "No Activity" and add OpenCV to your project. (Refer to https://github.com/DeLaSalleUniversity-Manila/opencvcamerapreviewsample-melvincabatuan)

## Possible Errors:

* OpenCV.mk not found Error 

* Solution:

Modify 'Android.mk' include as follows:

```make
include /path/to/your/OpenCV-android-sdk/sdk/native/jni/OpenCV.mk
```
Ex. 
```make
LOCAL_PATH := $(call my-dir)

include $(CLEAR_VARS)

#OPENCV_CAMERA_MODULES:=off
OPENCV_INSTALL_MODULES:=on
#OPENCV_LIB_TYPE:=SHARED

include /home/cobalt/Android/OpenCV-android-sdk/sdk/native/jni/OpenCV.mk

LOCAL_SRC_FILES  := DetectionBasedTracker_jni.cpp
LOCAL_C_INCLUDES += $(LOCAL_PATH)
LOCAL_LDLIBS     += -llog -ldl

LOCAL_MODULE     := detection_based_tracker

include $(BUILD_SHARED_LIBRARY)
```

## Compile 

Ex.
```shell
~/AndroidStudioProjects/OpenCV3-FaceDetection/app/jni$ ndk-build
[armeabi-v7a] Compile++ thumb: detection_based_tracker <= DetectionBasedTracker_jni.cpp
[armeabi-v7a] Prebuilt       : libopencv_java3.so <= /home/cobalt/Android/OpenCV-android-sdk/sdk/native/jni/../libs/armeabi-v7a/
[armeabi-v7a] SharedLibrary  : libdetection_based_tracker.so
/home/cobalt/Android/adt-bundle-linux-x86-20131030/android-ndk-r10d/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86/bin/../lib/gcc/arm-linux-androideabi/4.8/../../../../arm-linux-androideabi/bin/ld: warning: hidden symbol '__aeabi_atexit' in /home/cobalt/Android/adt-bundle-linux-x86-20131030/android-ndk-r10d/sources/cxx-stl/gnu-libstdc++/4.8/libs/armeabi-v7a/thumb/libgnustl_static.a(atexit_arm.o) is referenced by DSO /home/cobalt/AndroidStudioProjects/OpenCV3-FaceDetection/app/obj/local/armeabi-v7a/libopencv_java3.so
[armeabi-v7a] Install        : libdetection_based_tracker.so => libs/armeabi-v7a/libdetection_based_tracker.so
[armeabi-v7a] Install        : libopencv_java3.so => libs/armeabi-v7a/libopencv_java3.so
```
