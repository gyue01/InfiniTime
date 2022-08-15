# Build and download firmware using Win10 system
This document discuss how to compile the infinitime code under win10 environment and download the compiled firmware to PineTime watch. It is based on the information on other doc files on github project page. Currently the following methods works for infinitime 1.10 tagged branch.
## Prepare software on win10 computer
1. Install Microsoft Visual Studio Code (VS Code) with extensions: C/C++, CMake Tools, and any recommanded when open the project
2. Install docker software
3. Install github desktop app
## Setup compile environment
1. use github desktop app to make a clone of the infinitime code on the local computer
2. under github app choose the master branch tagged 1.10 (or other versions)
3. then use the visual studio code to open the infinitime folder.
4. wait for visual studio code to run docker container, then open an terminal. The terminal should show linux running with infinitime account name and on the /workspaces/InfiniTime folder. This indicates the docker environment run properly.
5. Add root account password to docker such that you can install missing packages to the docker image.
    - In VS Code-> explorer -> open .devcontainer/Dockerfile
    - Add the following into Dockerfile to give root account password "Docker!" or whatever.
    ```
    RUN echo 'root:Docker!' | chpasswd
    ```
6. Install npm package and the lv_font_conv package. In docker terminal,
    ```
    su
    apt-get update
    apt-get install npm
    npm install lv_font_conv
    exit
    ```
## Compile the Intinitime firmware
1. Go to /workspaces/InfiniTime in the docker terminal
2. Fix some files' format
    ```
    dos2unix src/displayapp/fonts/jetbrains_mono_bold_20.c_*
    ```
3. Generate build files
    ```
    /opt/create_build_open_ocd.sh
    ```
3. build the firmware
    ```
    cd build
    make -j pinetime-app
    ```
## Package the firmware to be downloaded by Gadgetbridge
