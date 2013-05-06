# Author: Yunhui Fu <yhfudev@gmail.com>
# License: GPL v3.0
#CC=g++

bin_PROGRAMS=gant
gant_SOURCES= \
    antlib.c \
    gant.c \
    $(NULL)

gant_DEPENDENCIES= \
    #$(top_builddir)/src/libgant.a \
    $(NULL)

#dumpyddic_LDADD = \
    $(top_builddir)/src/libgant.a \
    $(NULL)

DEFS+= \
    `getconf LFS_CFLAGS` \
    `getconf LFS64_CFLAGS` \
    -D_GNU_SOURCE \
    -D_FILE_OFFSET_BITS=64 \
    -DHAVE_MMAP64=1 \
    $(NULL)

INCLUDES= \
    -I $(top_srcdir)/include/ \
    -I $(top_builddir)/include/ \
    $(NULL)

AM_LDFLAGS= \
    -L $(top_builddir)/src/ \
    `getconf LFS_LDFLAGS` \
    `getconf LFS64_LDFLAGS` \
    $(NULL)

LDADD=
LDADD+= -lm -lpthread

if DEBUG
# use "valgrind --tool=memcheck --leak-check=yes" to check memory leak, MemWatch will drag the program.
#DEFS+=-DMEMWATCH
DEFS+= -DDEBUG=1
AM_CFLAGS=-g -Wall
#CFLAGS=-g -Wall
AM_CXXFLAGS=-g -Wall

else
#AM_CFLAGS=-O3 -Wall
AM_CFLAGS=-O3 -Wall
AM_CXXFLAGS=-O3 -Wall
endif

AM_CFLAGS+=-fpermissive
AM_CXXFLAGS+=-fpermissive


EXT_FLAGS=
@MK@SVNNUMTMP=$(shell LC_ALL=C svn info | grep -i Revision | awk '{print $$2}')
@MK@ifeq ($(SVNNUMTMP),)
@MK@else
EXT_FLAGS+= -DSVN_VERSION="${SVNNUMTMP}"
@MK@endif
AM_CFLAGS+=$(EXT_FLAGS)
AM_CXXFLAGS+=$(EXT_FLAGS)
DEFS+=$(EXT_FLAGS)
