dnl#                                               -*- Autoconf -*-
dnl# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([FSMegaInfo],[1.0],[dts@apple.com])
AC_CONFIG_SRCDIR([AliasManager.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])
AC_CANONICAL_TARGET
AC_USE_SYSTEM_EXTENSIONS
AM_INIT_AUTOMAKE([foreign])
AM_MAINTAINER_MODE
xcsdkdir=""
AC_CHECK_PROGS([XCRUN],[xcrun])
if test -n "${XCRUN}"; then
  if test -z "${MAKE}"; then
    dnl# Call the variable MAKE_PROG, not MAKE, to avoid confusion with
    dnl# SET_MAKE and with the usual MAKE variable that 'make' itself uses.
    AC_CHECK_PROG([MAKE_PROG],[make],[yes])
    if test -z "${MAKE_PROG}"; then
      MAKE="${XCRUN} MAKE"
      export MAKE
      xcsdkdir=`${XCRUN} --show-sdk-path 2>/dev/null`
      AC_MSG_NOTICE([xcsdkdir is "${xcsdkdir}"])
      AC_SUBST([xcsdkdir])
    fi
  fi
fi
AM_CONDITIONAL([HAVE_CORRECT_SYSROOT],
               [test -d /Developer/SDKs/MacOSX10.5.sdk])dnl

# Checks for programs.
AC_PROG_CPP
AM_PATH_PYTHON
AC_CACHE_CHECK([whether the compiler is actually clang],[ac_cv_clang],
  [AC_COMPILE_IFELSE(
     [AC_LANG_PROGRAM([[
	  #ifndef __clang__
	    #error "not clang"
	  #endif /* !__clang__ */
        ]])],
     [ac_cv_clang=yes],
     [ac_cv_clang=no])])dnl

# Checks for header files.
AC_HEADER_ASSERT
AC_HEADER_DIRENT
AC_HEADER_MAJOR
AC_HEADER_STAT
AC_HEADER_STDBOOL dnl# also "_CHECK"s it
AC_CHECK_HEADERS([assert.h dirent.h fts.h grp.h limits.h \
                  membership.h netdb.h netinet/in.h paths.h \
                  pwd.h sys/mount.h sys/param.h sys/vnode.h \
                  sys/xattr.h])
# These headers are OSX specific, and in frameworks:
AC_CHECK_HEADERS([CoreServices/CoreServices.h \
                  DiskArbitration/DiskArbitration.h])dnl

# Keep autoscan happy:
if test "x${ac_cv_header_inttypes_h}" = "x"; then
  test -z "${ac_cv_header_inttypes_h}" || unset ac_cv_header_inttypes_h
  AC_CHECK_HEADERS([inttypes.h])
fi
if test "x${ac_cv_header_stdint_h}" = "x"; then
  test -z "${ac_cv_header_stdint_h}" || unset ac_cv_header_stdint_h
  AC_CHECK_HEADERS([stdint.h])
fi
if test "x${ac_cv_header_unistd_h}" = "x"; then
  test -z "${ac_cv_header_unistd_h}" || unset ac_cv_header_unistd_h
  AC_CHECK_HEADERS([unistd.h])
fi

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
                strtoimax strlen strncmp strtoll])dnl

# Checks for declarations.
AC_CHECK_DECLS([VT_UNION],[],[],[
#ifdef HAVE_SYS_VNODE_H
# include <sys/vnode.h>
#else
# if defined(__GNUC__) && !defined(__STRICT_ANSI__)
#  warning "conftest for VT_UNION expects <sys/vnode.h> to be included."
# endif /* __GNUC__ && !__STRICT_ANSI__ */
#endif /* HAVE_SYS_VNODE_H */
])dnl

# Output:
AC_CONFIG_FILES([Makefile
                 Tests/Makefile])
AC_OUTPUT
