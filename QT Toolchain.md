# QT Toolchain use

## QT Toolchain cross-compile

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

### For configure.in, include these lines:

     AC_INIT(hello,0.1)
     
     AM_INIT_AUTOMAKE([foreign])
     
     AC_PROG_CC
     
     AC_PROG_INSTALL
     
     AC_OUTPUT(Makefile)
     
     source /opt/poky/2.4/environment-setup-i586-poky-linux
     
 ### aclocal
 ### autoconf
 
 
 
 
 
