# QT Toolchain use

## QT Toolchain cross-compile
https://www.yoctoproject.org/docs/1.7/adt-manual/adt-manual.pdf

http://www.yoctoproject.org/docs/latest/adt-manual/adt-manual.html#sdk-working-projects

$ mkdir $HOME/helloworld

$ cd $HOME/helloworld

#include <stdio.h>

main()

   {
   
      printf("Hello World!\n");
      
   }
   
### For Makefile.am, include these lines:

     bin_PROGRAMS = hello
     
     hello_SOURCES = hello.c

### For configure.ac, include these lines:

     AC_INIT(hello,0.1)
     
     AM_INIT_AUTOMAKE([foreign])
     
     AC_PROG_CC
     
     AC_PROG_INSTALL
     
     AC_OUTPUT(Makefile)
     
     source /opt/poky/2.4/environment-setup-i586-poky-linux
     
 ### aclocal
 ### autoconf
 ### touch NEWS README AUTHORS ChangeLog
 ### automake -a
 ### ./configure ${CONFIGURE_FLAGS}
 ### edit Makefile arm-poky-linux-gnueabi (後面加上-lm)
 ### make
 ### make install DESTDIR=./tmp
 ### file ./tmp/usr/local/bin/hello
 ### ./hello
 
