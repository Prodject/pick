AC_PREREQ([2.61])
AC_INIT([pick], [2.0.2], [pick-maintainers@calleerlandsson.com])
AM_INIT_AUTOMAKE([subdir-objects])
AC_CONFIG_HEADERS([config.h])
AC_PROG_CC
AM_PROG_CC_C_O
AC_CHECK_FUNCS([pledge reallocarray strtonum])
AC_SEARCH_LIBS([setupterm], [curses], [], [
  AC_SEARCH_LIBS([setupterm], [ncursesw],
    [AC_DEFINE([HAVE_NCURSESW_H], [1], [Define if ncursesw is available])],
    [PKG_CHECK_MODULES([NCURSES], [ncurses], [], [
      PKG_CHECK_MODULES([NCURSES], [ncursesw],
        [AC_DEFINE([HAVE_NCURSESW_H], [1], [Define if ncursesw is available])]
      )]
    )]
  )
])
AC_DEFUN([AC_MALLOC_OPTIONS], [
  AC_CANONICAL_HOST
  AC_MSG_CHECKING([for $host_os malloc hardening options])
  case "$host_os" in
  openbsd*) malloc_options="RS";;
  *)        malloc_options="";;
  esac
  if test -n "$malloc_options"; then
    AC_MSG_RESULT([$malloc_options])
  else
    AC_MSG_RESULT([no])
  fi
  AC_SUBST([MALLOC_OPTIONS], [$malloc_options])
])
AC_MALLOC_OPTIONS
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
