# 68k-tools
Docker image containing tools for 68000 development.  The tools include:
* gnu 68000 C++ cross compiler
* gnu 68000 cross assembler
* gnu 68000 cross linker
* srec_cat, etc.
* cpmtools
* git

To build:

    cd docker
    docker build -t 68k-tools .
  
To execute:

    docker run -it --rm -v /home/myuser/work:/opt/work 68-tools bash
    
