#
# TextParser - Text Parsing Library
#
# Copyright (C) 2012-2013 Institute of Industrial Science, The University of Tokyo.
# All rights reserved.
#

EXTRA_DIST=Makefile_hand

#libdir=../lib

if MPI
LIBFORMPI=../lib/libTextParser_mpi.la
___lib_libTextParser_mpi_la_SOURCES=TextParser.cpp TextParserTree.cpp TextParserElement.cpp
___lib_libTextParser_mpi_la_CXXFLAGS=-I../include -DBUILD_MPI
else
LIBFORMPI=
endif
libTextParser_mpi_la_OBJ=$(___lib_libTextParser_mpi_la_SOURCES:.cpp=.o)


if FORTRAN
LIBFORFORTRAN=../lib/libTextParser_f90api.la
___lib_libTextParser_f90api_la_SOURCES=TextParser_fapi.f90
TextParser_fapi.o:../include/TextParser.inc ../include/TextParser.h
else
LIBFORFORTRAN=
endif
libTextParser_f90api_la_OBJ=$(___lib_libTextParser_f90api_la_SOURCES:.f90=.o)


lib_LTLIBRARIES = ../lib/libTextParser.la ${LIBFORFORTRAN} ${LIBFORMPI}

dotalibs=$(lib_LTLIBRARIES:.la=.a)

___lib_libTextParser_la_SOURCES=TextParser.cpp TextParserTree.cpp TextParserElement.cpp
libTextParser_la_OBJ=$(___lib_libTextParser_la_SOURCES:.cpp=.o)

FCFLAGS=-I../include 
CXXFLAGS=-I../include 
#libTextParser_la_CXXFLAGS=-I../include 
#libTextParser_f90api_la_FCFLAGS=-I../include
CLEANFILES= ${lib_LTLIBRARIES} ${dotalibs} 
DISTCLEANFILES=*~ ${lib_LTLIBRARIES} ${dotalibs}

LDFLAGS= -version-info 1:3

TextParser.o : ../include/TextParser.h ../include/TextParserTree.h ../include/TextParserCommon.h ../include/TextParserElement.h
TextParserTree.o: ../include/TextParserTree.h ../include/TextParserCommon.h ../include/TextParserElement.h
TextParserElement.o: ../include/TextParserCommon.h ../include/TextParserElement.h
