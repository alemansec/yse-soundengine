# This is libYSE 2.0 #

libYSE is a cross platform sound engine, written in C++. The 1.0 version was built with JUCE, but because of possible licensing isssues and the current JUCE being unable to create usable Android libraries, JUCE support is removed in libYSE 2.0. Currently Windows, Linux and Android are supported. 

### Nuget ###
If you use YSE with C#, a few nuget packages are available. For windows you need [https://www.nuget.org/packages/Yse.NET.Standard/](Yse.NET.Standard). _(YSE.NET.PCL is a dependency and will be loaded automatically.)_

With Android, you can use [https://www.nuget.org/packages/Yse.NET.Android/](Yse.NET.Android).
For Xamarin Forms, add Yse.NET.Android and YSE.NET.PCL to your Android Project, and add YSE.NET.PCL to your Xamarin Forms project. An example of this usage is available in the Demo.Xamarin.Forms project inside this repository.

### Windows Support ###
There is a native C++ library, compiled with Visual Studio. It uses libsndfile and portaudio a backends.
A .NET framework library is also included.

### Android Support ###
The native android library is also created with Visual Studio. It uses libsndfile and openSLES backends. Compiling it on linux should be possible if you create the makefile to do that. 

The .NET android library also provides support for C# Android applications in visual studio. Using Xamarin Forms is also possible.

There is one drawback right now: I could not find a way to pass the asset manager to the native library, making it impossible to read assets from an apk. I will work on that later. For now, a workaround is to use the BufferIO class. By reading audio files into a memory buffer, they can be passed to libYSE from .NET. This is not ideal if you have big audio files though.

### Linux Support (thanks to user [noondie](https://github.com/noondie)) ###
Building on Linux is supported by cmake.
PortAudio and libsndfile are the only dependencies for YSE.
Do the following in the main directory 

```
$mkdir build 
$cd build 
$cmake ..
```

### iOS/Mac Support ###
This was also supported in YSE 1.0, but had to go when I decided to remove the dependency on JUCE. Adding support would mean adding other backends for reading files _(which is done by libsndfile now)_ and streaming audio output _(openSLES on Android and portaudio on Windows)_. The library is currently written with supporting multiple backends in mind, so it can't be that hard. Currently I don't have time to do this though.

### Libraries ###
Native C++ libraries are working, as well as libraries for C# _(.NET framework and .NET standard)_. The project also includes wrappers for use with xamarin forms.

### Demo ###
Demo projects are also included for Windows _(Native/C++ and WPF/C#)_, Android _(Native/C++, Android.NET/C# and Xamarin.Forms)_. 


