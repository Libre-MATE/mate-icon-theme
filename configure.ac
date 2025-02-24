#   Copyright (C) 2022  Libre MATE
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA

AC_INIT([mate-icon-theme],
        [1.26.0],
        [https://github.com/Libre-MATE/mate-icon-theme/issues],
        [mate-icon-theme],
        [https://github.com/Libre-MATE/mate-icon-theme/])
AC_PREREQ(2.53)
AC_COPYRIGHT([Copyright (C) 2022 Libre MATE])
AC_CONFIG_SRCDIR([index.theme.in.in])
AM_EXTRA_RECURSIVE_TARGETS([clean-png-icons build-png-icons])
AM_INIT_AUTOMAKE([1.11 tar-ustar dist-xz no-dist-gzip foreign check-news])
AM_SILENT_RULES([yes])

PKG_PROG_PKG_CONFIG([0.19])

AM_GNU_GETTEXT_VERSION([0.19.8])
AM_GNU_GETTEXT_REQUIRE_VERSION([0.19.8])
AM_GNU_GETTEXT([external])

GETTEXT_PACKAGE=AC_PACKAGE_NAME
AC_SUBST(GETTEXT_PACKAGE)
localedir='$(datadir)/locale'
AC_SUBST(localedir)

# Workaround to make aclocal get the right flags
AC_SUBST(ACLOCAL_AMFLAGS, "\${ACLOCAL_FLAGS}")

# Define the toplevel path here
AC_SUBST(themedir, "\${datadir}/icons/mate")

# Input and Output dirs for the rendering
AC_SUBST(SVGSRCDIR, "src")
AC_SUBST(SVGOUTDIR, "mate")

# Icon sizes we want to install
AC_SUBST([render_sizes], ["8x8 16x16 22x22 24x24 32x32 48x48 256x256"])

# Allow icon mapping to be disabled
AC_ARG_ENABLE([icon-mapping],
    AS_HELP_STRING([--enable-icon-mapping],
                   [Enable compatibility symlinks [default=auto]]),
                   [enable_mapping=$enableval],
                   [enable_mapping=yes])

ICONMAP="true"
if test "x$enable_mapping" != "xno"; then
   UTILS_REQUIRED=0.8.7

   AC_MSG_CHECKING([icon-naming-utils >= $UTILS_REQUIRED])
   PKG_CHECK_EXISTS(icon-naming-utils >= $UTILS_REQUIRED,
                    have_utils=yes, have_utils=no)
   if test "x$have_utils" = "xyes"; then
      UTILS_PATH="`$PKG_CONFIG --variable=program_path icon-naming-utils`"
      ICONMAP="$UTILS_PATH/icon-name-mapping"
      AC_MSG_RESULT([yes])
   else
      AC_MSG_RESULT([no])
      AC_MSG_ERROR([icon-naming-utils >= $UTILS_REQUIRED is required to build
                    and install mate-icon-theme])
   fi
else
   ICONMAP="false"
fi

AC_SUBST(ICONMAP)

AC_CONFIG_FILES([
Makefile
po/Makefile.in
src/Makefile
menta/Makefile
mate/Makefile
mate/8x8/Makefile
mate/8x8/emblems/Makefile
mate/16x16/Makefile
mate/16x16/actions/Makefile
mate/16x16/apps/Makefile
mate/16x16/categories/Makefile
mate/16x16/devices/Makefile
mate/16x16/emblems/Makefile
mate/16x16/mimetypes/Makefile
mate/16x16/places/Makefile
mate/16x16/status/Makefile
mate/22x22/Makefile
mate/22x22/actions/Makefile
mate/22x22/apps/Makefile
mate/22x22/categories/Makefile
mate/22x22/devices/Makefile
mate/22x22/emblems/Makefile
mate/22x22/mimetypes/Makefile
mate/22x22/places/Makefile
mate/22x22/status/Makefile
mate/24x24/Makefile
mate/24x24/actions/Makefile
mate/24x24/apps/Makefile
mate/24x24/categories/Makefile
mate/24x24/devices/Makefile
mate/24x24/emblems/Makefile
mate/24x24/mimetypes/Makefile
mate/24x24/places/Makefile
mate/24x24/status/Makefile
mate/32x32/Makefile
mate/32x32/actions/Makefile
mate/32x32/apps/Makefile
mate/32x32/categories/Makefile
mate/32x32/devices/Makefile
mate/32x32/emblems/Makefile
mate/32x32/mimetypes/Makefile
mate/32x32/places/Makefile
mate/32x32/status/Makefile
mate/48x48/Makefile
mate/48x48/actions/Makefile
mate/48x48/apps/Makefile
mate/48x48/categories/Makefile
mate/48x48/devices/Makefile
mate/48x48/emblems/Makefile
mate/48x48/mimetypes/Makefile
mate/48x48/places/Makefile
mate/48x48/status/Makefile
mate/64x64/Makefile
mate/64x64/status/Makefile
mate/96x96/Makefile
mate/96x96/status/Makefile
mate/256x256/Makefile
mate/256x256/actions/Makefile
mate/256x256/apps/Makefile
mate/256x256/categories/Makefile
mate/256x256/devices/Makefile
mate/256x256/emblems/Makefile
mate/256x256/mimetypes/Makefile
mate/256x256/places/Makefile
mate/256x256/status/Makefile
mate/scalable/Makefile
mate/scalable-up-to-32/Makefile
])

AC_OUTPUT
