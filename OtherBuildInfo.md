
https://bitbucket.org/jjgalvez/iipsrv-openslide
I took this from above... not sure if it will elp or not



BUILDING:
-------- 
The standard autoconf build process should work fine. If you want to allow
dynamic loading of 3rd party image decoders, use the configure option
--enable-modules. There is a version of the FCGI development library included
in this distribution. The configure script will use this bundled version
unless it detects one already installed. Alternatively, you may specify the
path using --with-fcgi-incl=<path> and --with-fcgi-lib=<path>.

If this is an SVN or Git development version, first generate the autoconfigure
environment using autogen.sh:
./autogen.sh

Otherwise for release versions, use configure directly:

eg.
./configure
make

SPECIFIC BUILDING ON UBUNTU:
---------------------------
To build on Ubuntu install the following libraries:
libopenjp2-7-dev
libopenjp2-7 
libopenjpeg-dev 
openslide-tools
libopenslide-dev 
libopenslide0 
libjbig-dev 
liblzma-dev 
libtiff5-dev 
libtiffxx5 
libjpeg-dev 
libjpeg-turbo8-dev 
libjpeg8-dev 
memcached
libmemcached11
libmemcached-dev

link /usr/include/openslide/openslide-features.h and
/usr/include/openslide/openslide.h
to iipsrv-openlide/src

./autogen.sh

./configure
make

copy iipimagesrv.fcgi to a suitable location (/opt/iipimage)
change ownership to www-data (chown www-data:www-data iipimagesrv.fcgi)

see instructions below to connect iipimage to nginx. 
hint:  supervisord is a good option to manage iipimagesrv.fcgi
