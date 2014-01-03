#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([tp_fancontrol], [0.1])
AC_CONFIG_SRCDIR([src/tp_fancontrol.c])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC
AC_PROG_INSTALL

PKG_PROG_PKG_CONFIG

# Debug.
AC_ARG_ENABLE(debug, AC_HELP_STRING([--enable-debug],
        [enable compiling with debugging information]), [
        if (test "${enableval}" = "yes" && test "${ac_cv_prog_cc_g}" = "yes"); then
                CFLAGS="$CFLAGS -D__DEBUG__ -g"
        fi
])

# Systemd units.
AC_ARG_WITH([systemdsystemunitdir],
        AS_HELP_STRING([--with-systemdsystemunitdir=DIR], [Directory for systemd service files]),
        [], [with_systemdsystemunitdir=$($PKG_CONFIG --variable=systemdsystemunitdir systemd)])
if test "x$with_systemdsystemunitdir" != xno; then
        AC_SUBST([systemdsystemunitdir], [$with_systemdsystemunitdir])
fi

# Checks for libraries.
PKG_CHECK_MODULES([SYSTEMD], [libsystemd-daemon])

# Checks for header files.
AC_CHECK_HEADERS([locale.h stdlib.h string.h sys/time.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T

# Checks for library functions.
AC_FUNC_MALLOC
AC_FUNC_REALLOC
AC_CHECK_FUNCS([memset setlocale strdup])

AC_CONFIG_FILES([Makefile
                 src/Makefile])
AC_OUTPUT
