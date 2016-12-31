#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([palindrom], [0.1.0], [kmzhou4@yahoo.com])
AM_INIT_AUTOMAKE([-Wall -Werror])
AC_CONFIG_SRCDIR([src/checkpalindrome.cpp])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CC
AC_PROG_CXX
AC_PROG_INSTALL

AC_LANG([C], [C++])
AC_LANG_PUSH([C++])
AX_CXX_COMPILE_STDCXX_11([noext], [mandatory])

if test "$prefix" = "NONE"; then
	prefix=$ac_default_prefix
fi

# Checks for libraries.
LIBS="$LIBS -lkemin"
orpara_CXXFLAGS="-I$prefix/include/orpara"
orpara_LDFLAGS="-L$prefix/lib"
AC_ARG_VAR([ORPARAINC], [path for the orpara include directory. config or environment variable.])
AC_ARG_VAR([ORPARALIB], [path for the orpara lib directory])
if test -n "$ORPARAINC"; then
	orpara_CXXFLAGS=$ORPARAINC 
fi
if test -n "$ORPARALIB"; then
	orpara_LDFLAGS=$ORPARALIB 
fi
CXXFLAGS="$orpara_CXXFLAGS $CXXFLAGS"
LDFLAGS="$orpara_LDFLAGS $LDFLAGS"
AC_CHECK_HEADERS([bioseq.h], [], [AC_MSG_ERROR([unable to find orpara header])])
AC_LINK_IFELSE([AC_LANG_PROGRAM([#include <bioseq.h>], [orpara::bioseq dummy])],
    [HAVE_ORPARA=1; AC_MSG_NOTICE([orpara is installed])],
	 [AC_MSG_ERROR([orpara is not installed])])
AC_LANG_POP([C++])

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.
AC_CHECK_HEADER_STDBOOL

# Checks for library functions.

AC_CONFIG_FILES([Makefile
                 src/Makefile])
AC_OUTPUT
