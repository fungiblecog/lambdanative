# Introduction

LambdaNative is an open-source (BSD licensed) cross-platform
development environment written in Scheme (Gambit-C), supporting
Android, iOS, OS X, Linux, Windows and OpenBSD.

LambdaNative is actively developed and used at the
University of British Columbia by the Pediatric Anesthesia
Research Team for production of clinical mHealth
applications, including mission-critical embedded drug
delivery systems and telemonitoring apps for iPhone
and Android smartphones.  LambdaNative-based applications
have been used in clinical trials on >10,000 subjects in
Canada, France, India, Uganda, Bangladesh, and South
Africa, in >10 separate clinical studies:

[Petersen CL, Görges M, Dunsmuir D, Ansermino JM, Dumont GA. "Experience Report: Functional Programming of mHealth Applications". The 18th ACM SIGPLAN International Conference on Functional Programming, ICFP'13, Boston, MA, USA](http://ecem.ece.ubc.ca/~cpetersen/lambdanative_icfp13.pdf)

If you use the LambdaNative framework for your own work, please reference this paper.

A slideshow describing the LambdaNative framework is available [here](https://github.com/part-cw/lambdanative/blob/master/docs/LambdaNative.pdf?raw=true).

`uSquish`, the simple example game included in the LambdaNative repository,
is available as a free download on the Apple and Google stores:

[uSquish for iOS](https://itunes.apple.com/us/app/usquish/id647308142)

[uSquish for Android](https://play.google.com/store/apps/details?id=ca.bccw.usquish)

# [ LambdaNative Documentation Wiki ](./wiki/Home)

# Getting started

## Required SDKs

The minimum requirement for developing applications is the
presence of a working gcc compiler. In addition,
cross-compilation requires installation of the appropriate
environments:

### Android (mac or linux) 
1. Install the android SDK and NDK under `/usr/local` and the
API that you want to develop for.  You will need the "SDK
Tools", not the "ADT Bundle".  Once SDK and NDK are
installed, you should have an `android-sdk-*` and
`android-ndk-*` directory.  Make sure to set proper
permissions on the directories to allow your development
account full access.
2. Run `android` to install the APIs (minimum supported API is
8 (Android 2.2) without real-time audio, and API 10 (Android
2.3.3) with real-time audio).
3. Run `android avd` to setup an android virtual device with
your desired API.

### iOS (mac)
1. Install the iOS SDK. The iOS SDK is part of the Xcode
distribution. For XCode versions newer than 4.5 you also
need to install the matching "Command Line Tools". These
downloads can be found under "Downloads for Apple
Developers" in the iOS Dev Center.
2. Follow the standard online procedures to create an iOS
Development Certificate, and, optionally, an iOS
Distribution Certificate, and register your device(s) for 
development.
3. Use XCode to create and sync a Provisioning Profile onto
your device(s). The XCode build chain will not work properly
if you do this step outside of XCode.

### Linux cross-compilation (mac)
Install a linux cross-compiler under `/usr/local` to create
linux binaries.

### Windows cross-compiler (mac or linux)
Install a windows cross-compiler under `/usr/local` to
create windows binaries.

### Windows development environment
If you are developing on a windows machine (not
recommended), install the MSYS development environment.

## Required tools

A number of tools are needed to support the framework.
Please ensure that these are installed on your system:

* `wget` for pulling library code from the net
* `freetype` for rendering vector fonts
* `netpbm` and `ImageMagick` for misc pixmap manipulation
* `ghostscript` for converting vector artwork
* `cmake` for generating XCode projects
* `latex` for generating string textures (actually uses the unicode `xelatex`)
* `tgif` for editing vector artwork (optional)
* `fruitstrap` for installing iOS apps (optional)

## SETUP and PROFILE

Use the provided `SETUP.template` and `PROFILE.template` to
create files `SETUP` and `PROFILE` in the framework
directory matching your setup.

## First build

To start using the framework, type:

    ./configure DemoHelloWorld
    make

this will take a while, as the supporting libraries are
downloaded and compiled for the first time. On completion,
you will have a binary for your local host.

On a suitably configured platform, you can now do:
    
    ./configure DemoHelloWorld android
    make

    ./configure DemoHelloWorld ios
    make

and binaries for the specified platforms will be built and
packaged.

## Directory structure

    apps/                       applications
    libraries/                  supporting libraries
    modules/                    application modules
    modules/config              application configuration
    modules/eventloop           event handling for GUI applications
    modules/ln_core             general supporting functions
    modules/ln_glcore           low level OpenGL wrapper
    modules/ln_glgui            widget based GUI
    modules/ln_audio            cross-platform audio handling
    bootstraps/                 platform launchers
    tools/pngtools              png texture generator
    tools/ttftools              ttf texture generator

