#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])

m4_include([m4/version.m4])

AC_INIT([quvi], [_QUVI_VERSION],
  [http://sourceforge.net/apps/trac/quvi/], [],
  [http://quvi.sourceforge.net/])

AC_CONFIG_SRCDIR([src/quvi/quvi.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_AUX_DIR([config.aux])
AC_CONFIG_MACRO_DIR([m4])

AC_CANONICAL_SYSTEM
AC_GNU_SOURCE

AC_DEFINE_UNQUOTED([CANONICAL_TARGET], "$target", [...])
AC_DEFINE_UNQUOTED([CANONICAL_HOST], "$host", [...])

AM_INIT_AUTOMAKE([-Wall -Werror foreign dist-bzip2 dist-xz])
AM_SILENT_RULES([yes])

# Checks for programs.
AC_PROG_CC

# Checks for libraries.
PKG_CHECK_MODULES([libquvi], [libquvi >= 0.4.0])
PKG_CHECK_MODULES([libcurl], [libcurl >= 7.18.2])

# Checks for header files.
AC_CHECK_HEADERS([stdarg.h stdlib.h string.h stddef.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_CHECK_TYPES([ptrdiff_t])
AC_TYPE_SIZE_T

# Checks for library functions.
AC_CHECK_FUNCS([memset strchr strcspn strdup strerror strspn strstr strtol])
AC_FUNC_REALLOC
AC_FUNC_MALLOC

have_asprintf=no
AC_CHECK_FUNCS([vasprintf], [
  AC_CHECK_FUNCS([asprintf], [have_asprintf=yes])
])
AM_CONDITIONAL([NO_ASPRINTF], [test x"$have_asprintf" != "xyes"])

# Version.
VN=`$srcdir/gen-ver.sh $srcdir`
AC_DEFINE_UNQUOTED([VN],["$VN"], [We have version number from gen-ver.sh])

# --with-manual
AC_ARG_WITH([manual],
  [AS_HELP_STRING([--with-manual],
    [install manual page(s) @<:@default=yes@:>@])],
  [],
  [with_manual=yes])
AM_CONDITIONAL([WITH_MANUAL], [test x"$with_manual" != "xno"])

AC_CONFIG_FILES([
  Makefile
  doc/Makefile
  doc/man1/Makefile
  src/Makefile
  src/quvi/Makefile])
AC_OUTPUT

AC_MSG_NOTICE([
  version:        ${VERSION} (${VN})
  host setup:     ${host}
  compiler:       ${CC}
  cflags:         ${CFLAGS}
  prefix:         ${prefix}
  install manual: ${with_manual}])
