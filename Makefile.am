AM_CPPFLAGS = $(THREAD_CFLAGS) $(DVDREAD_CFLAGS) -I$(top_srcdir)/src

EXTRA_DIST = autogen.sh \
	     AUTHORS \
	     ChangeLog \
	     COPYING \
	     INSTALL \
	     README \
	     TODO \
	     msvc/ \
	     src/README.MAP \
	     src/FELLOWSHIP.map \
	     docs/doxy.conf \
	     docs/mainpage.cpp \
	     docs/tutorial.cpp \
	     docs/dvd_structures \
	     docs/library_layout

lib_LTLIBRARIES = libdvdnav.la

libdvdnav_la_SOURCES = \
	src/dvdnav.c \
	src/read_cache.c \
	src/navigation.c \
	src/highlight.c \
	src/searching.c \
	src/settings.c \
	src/remap.c \
	src/dvdnav_internal.h \
	src/read_cache.h \
	src/remap.h \
	src/vm/decoder.c \
	src/vm/decoder.h \
	src/vm/vm.c \
	src/vm/vm.h \
	src/vm/vmcmd.c \
	src/vm/vmcmd.h

libdvdnav_la_LDFLAGS = \
	-version-info $(DVDNAV_LT_CURRENT):$(DVDNAV_LT_REVISION):$(DVDNAV_LT_AGE) \
	-export-symbols-regex "^dvdnav"
libdvdnav_la_LIBADD = $(THREAD_LIBS) $(DVDREAD_LIBS)

pkgincludedir = $(includedir)/dvdnav

pkginclude_HEADERS = \
	src/dvdnav/dvdnav.h \
	src/dvdnav/dvdnav_events.h \
	src/dvdnav/dvd_types.h

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = misc/dvdnav.pc misc/dvdnavmini.pc

EXTRA_PROGRAMS = menus

menus_SOURCES = examples/menus.c
menus_CPPFLAGS = $(AM_CPPFLAGS) -DDVDNAV_COMPILE
menus_LDADD = libdvdnav.la

docs: misc/doxy.conf
	@if test x"$(DOXYGEN)" != "xno"; then \
	  cd misc && $(DOXYGEN) doxy.conf > /dev/null 2> /dev/null; \
	fi
