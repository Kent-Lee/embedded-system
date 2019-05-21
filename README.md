# Music Player

This is the final group project for CMPT 433 Embedded Systems course. The objective is to use BeagleBone Green, Zen Cape, and 16x32 RGB LED Matrix to build a music player.

## Instructions

1. install `mpg123` library on target (BBG & Zen Cape)

    ```bash
    apt-get install mpg123
    ```

2. copy `libmpg123.so.0` on target to directory `asound\_lib\_BBB`, then rename it to `libmpg123.so`

    ```bash
    cd /usr/lib/arm-linux-gnueabihf/
    cp libmpg123.so.0 /mnt/remote/asound_lib_BBB/libmpg123.so
    ```

    Troubleshooting: if `libmpg123.so.0` is not there, run the following to find the file path

    ```bash
    ldconfig -p | grep libmpg123.so.0 
    ```

3. connect the LED matrix as described in our BBG LED matrix guide. Mount the `~/cmpt433/public` folder

    ```bash
    mnt/remote/myApps/cmpt433_proj/wave_player
    ```

4. on the host (your PC), navigate to the project root directory. The wave-files folder is for storing music files. Ensure that at least one `wav` or `mp3` file is inside that folder, then compile the program

    ```bash
    make
    ```

    Troubleshooting: if you get the error `fatal error: mpg123.h no such file or directory`, run

    ```bash
    sudo apt-get install libmpg123-dev
    ```

5. on the target, navigate to the shared folder. A directory named `cmpt433_proj` will be created from the previous step; navigate to there and run the executable file

    ```bash
    ./wave_player
    ```

## Contributors

- David Tan
- Raymond Chan
- Kent Lee
- Regan Lam