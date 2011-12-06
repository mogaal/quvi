
EXTRA_DIST=	cmdline.ggo

src=	cmdline.c quvi.c strepl.c
hdr=	cmdline.h platform.h

if NO_ASPRINTF
src+=	vasprintf.c
src+=	asprintf.c
endif

bin_PROGRAMS=	quvi
quvi_SOURCES=	$(src) $(hdr)

quvi_CPPFLAGS=\
 $(libquvi_CFLAGS) \
 $(libcurl_CFLAGS) \
 $(AM_CPPFLAGS)

quvi_CFLAGS=\
 $(AM_CFLAGS)

quvi_LDFLAGS=\
 $(AM_LDFLAGS)

quvi_LDADD=\
 $(libquvi_LIBS) \
 $(libcurl_LIBS) \
 $(LIBICONV) \
 $(LTLIBICONV)
