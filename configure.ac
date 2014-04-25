#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([FSMegaInfo],[1.0],[dts@apple.com])
AC_CONFIG_SRCDIR([AliasManager.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])
AC_CANONICAL_TARGET
AC_USE_SYSTEM_EXTENSIONS
AM_INIT_AUTOMAKE([foreign])
AM_CONDITIONAL([HAVE_CORRECT_SYSROOT],
               [test -d /Developer/SDKs/MacOSX10.5.sdk])

# Checks for programs.
AC_PROG_CPP
AM_PATH_PYTHON

# Checks for header files.
AC_HEADER_ASSERT
AC_HEADER_DIRENT
AC_HEADER_MAJOR
AC_HEADER_STAT
AC_HEADER_STDBOOL dnl# also "_CHECK"s it
AC_CHECK_HEADERS([assert.h fts.h grp.h limits.h membership.h \
                  netdb.h netinet/in.h paths.h pwd.h stdio.h \
                  sys/mount.h sys/param.h sys/vnode.h sys/xattr.h])
# These headers are OSX specific, and in frameworks:
AC_CHECK_HEADERS([CoreServices/CoreServices.h \
                  DiskArbitration/DiskArbitration.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_SYS_LARGEFILE
AC_SYS_LONG_FILE_NAMES
AC_C_BIGENDIAN
AC_C_CONST
AC_C_PROTOTYPES
AC_STRUCT_DIRENT_D_INO
AC_STRUCT_DIRENT_D_TYPE
AC_TYPE_GETGROUPS dnl# also checks "_UID_T"
AC_TYPE_INT8_T
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_INTMAX_T
AC_TYPE_INTPTR_T
AC_TYPE_MODE_T
AC_TYPE_OFF_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_CHECK_MEMBERS([struct stat.st_blksize])
AC_STRUCT_ST_BLOCKS
AC_CHECK_MEMBERS([struct stat.st_rdev])
AC_CHECK_MEMBERS([struct statfs.f_reserved1])
AC_TYPE_UINT8_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINTMAX_T
AC_TYPE_UINTPTR_T

# Checks for library functions.
AC_FUNC_CLOSEDIR_VOID
AC_FUNC_LSTAT dnl# also checks whether it "_FOLLOWS_SLASHED_SYMLINK"
AC_FUNC_MALLOC
AC_FUNC_MEMCMP
AC_FUNC_STAT
AC_FUNC_STRFTIME
AC_CHECK_FUNCS([fprintf memset pathconf sscanf strcasecmp strerror \
                strtoimax strlen strncmp strtoll])

# Output:
AC_CONFIG_FILES([Makefile
                 Tests/Makefile])
AC_OUTPUT
