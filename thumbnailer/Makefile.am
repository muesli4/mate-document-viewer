bin_PROGRAMS = atril-thumbnailer

atril_thumbnailer_SOURCES = \
	atril-thumbnailer.c

atril_thumbnailer_CPPFLAGS = \
	-DATRILDATADIR=\"$(pkgdatadir)\"	\
	-I$(top_srcdir)				\
	-I$(top_builddir)			\
	-DMATELOCALEDIR=\"$(datadir)/locale\"	\
	-DMATEICONDIR=\""$(datadir)/pixmaps"\" \
	$(AM_CPPFLAGS)

atril_thumbnailer_CFLAGS = \
	$(FRONTEND_CFLAGS)	\
	$(DISABLE_DEPRECATED)	\
	$(WARN_CFLAGS)		\
	$(AM_CFLAGS)

atril_thumbnailer_LDFLAGS = $(AM_LDFLAGS)

if PLATFORM_WIN32
atril_thumbnailer_LDFLAGS += -mwindows
endif

atril_thumbnailer_LDADD = \
	$(top_builddir)/libdocument/libatrildocument.la	\
	$(FRONTEND_LIBS)

thumbnailerdir = $(datadir)/thumbnailers
thumbnailer_in_files = atril.thumbnailer.in
thumbnailer_DATA = $(thumbnailer_in_files:.thumbnailer.in=.thumbnailer)


atril.thumbnailer: $(thumbnailer_in_files)
	$(AM_V_GEN)sed \
		-e "s|\@ATRIL_MIME_TYPES\@|$(ATRIL_MIME_TYPES)|" \
		$< > $@

EXTRA_DIST =         	\
	$(thumbnailer_in_files)

DISTCLEANFILES = \
	$(thumbnailer_DATA)

-include $(top_srcdir)/git.mk
