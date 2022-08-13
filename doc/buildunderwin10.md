1. use github desktop app to make a clone of the infinitime code.
2. under github app choose the master branch tagged 1.10
3. then use the visual studio code to open the infinitime folder.
4. wait for visual studio code to run docker container, then opened an terminal
5. with root account
add root password add in to dockerfile RUN echo 'Docker!' | passwd --stdin root 
apt-get install npm
npm install lv_font_conv
6. runs the create_build_open_ocd.sh
 /workspaces/InfiniTime$ cmake -G 'Unix Makefiles' -DCMAKE_BUILD_TYPE=Release -DUSE_OPENOCD=1 -DARM_NONE_EABI_TOOLCHAIN_PATH=/opt/gcc-arm-none-eabi-9-2020-q2-update -DNRF5_SDK_PATH=/opt/nRF5_SDK_15.3.0_59ac345 -S . -Bbuild
7. cd build
8 make -j pinetime-app