### Darwin-OP patch
patch to ubuntu 2018 or latest

#### --- Download file
> https://sourceforge.net/projects/darwinop/files/Software/Main%20Controller/Source%20Code/

#### --- Environtment
- sudo usermod -a -G dialout $USER
- sudo reboot
- sudo apt-get update
- sudo apt install openssh-server 
- sudo apt install apache2
- sudo apt install make
- sudo apt-get install g++ manpages-dev libjpeg62-dev libncurses5-dev git

#### --- Install opencv
- sudo apt-get install libopencv-dev -y

#### --- Remote Desktop
- <a href="https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/"> cara install remote desktop</a>


#### --- Program change
step 1. change camera.h <br>
change

		static const double VIEW_V_ANGLE = 46.0; //degree
		static const double VIEW_H_ANGLE = 58.0; //degree
to

		static constexpr double VIEW_V_ANGLE = 46.0; //degree
		static constexpr double VIEW_H_ANGLE = 58.0; //degree
    
step 2. clean <br>
- go to directory  Linux/build
- make clean


step 3. add library unistd <br>
- go to Framework/include/motionManager.h
- add #include <unistd.h>
- go to Linux/project/demo/VisionMode.cpp
- add #include <unistd.h>

step 4. add library stat <br>
- go to Linux/include/LinuxCamera.h
- add #include <sys/stat.h>

step 5. build <br>
- go to directory  Linux/build
- make all

step 6. pthread <br>
- open Makefile in demo
- change

      LFLAGS += -lpthread -ljpeg -lrt
- to
 
      LFLAGS += -pthread -ljpeg -lrt
      
step 7. flag <br>
- move $(LFLAGS) to end

#### --- Author
> Danu andrean | RSCUAD
