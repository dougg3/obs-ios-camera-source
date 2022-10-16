<div align = "center">
<img src=".github/obs-logo.svg" width="128" height="128" />
</div>


obs-ios-camera-source Linux branch
==============
This is a fork of [obs-ios-camera-source](https://github.com/wtsnz/obs-ios-camera-source) that supports Linux.

To use this you use the [accompanying iOS app](https://obs.camera/) to begin streaming in OBS.

## Downloads

### Ubuntu 22.04 (and possibly other distros), 20.04, and 18.04  
(Confirmed working on Manjaro as of 06 Oct 2022 by [@seffyroff](https://github.com/seffyroff))

Go to the [releases](https://github.com/dougg3/obs-ios-camera-source/releases) section of this repository and download the latest release. After downloading, place the zip file in your home directory and run:

```
unzip plugin-ubuntu-*.zip
```

You must have the `unzip` package installed for this to work: `sudo apt install unzip`.

## Building

These instructions are tested on Ubuntu 22.04, 20.04, and 18.04. For other distros/versions, YMMV.

- Make sure you have the universe and multiverse repositories enabled so you will have access to FFmpeg.
- Install OBS Studio using the [instructions on the OBS wiki](https://obsproject.com/wiki/install-instructions#ubuntu-installation).
  - This should install the headers and CMake files necessary for compiling against libobs. It does on Ubuntu; I can't speak for other distros.
- Install prerequisites: `sudo apt install build-essential git cmake libavcodec-dev libssl-dev pkg-config`
  - Note: On Fedora, the required package for OpenSSL is called openssl-devel.
- Download this plugin source code:
  - `git clone https://github.com/dougg3/obs-ios-camera-source.git`
- Build the plugin:
  - `cd obs-ios-camera-source`
  - `mkdir build`
  - `cd build`
  - `cmake ..`
  - `make -j$(nproc)`
- Manually install the plugin by copying relevant files into your OBS plugins directory (assuming 64-bit Linux):
  - `mkdir -p ~/.config/obs-studio/plugins/obs-ios-camera-source/data/locale`
  - `mkdir -p ~/.config/obs-studio/plugins/obs-ios-camera-source/bin/64bit`
  - `cp ../data/locale/en-US.ini ~/.config/obs-studio/plugins/obs-ios-camera-source/data/locale/`
  - `cp obs-ios-camera-source.so ~/.config/obs-studio/plugins/obs-ios-camera-source/bin/64bit/`

Note for Ubuntu 18.04 users: this plugin now requires a newer version of CMake than what was bundled originally. Either use the premade binaries, or [upgrade your CMake](https://apt.kitware.com/).

## Special thanks
- [wtsnz](https://github.com/wtsnz) for creating an awesome plugin/app for using your iOS camera in OBS!
