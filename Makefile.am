ACLOCAL_AMFLAGS = -I m4

AUX_DIST = \
	$(ac_aux_dir)/config.guess \
	$(ac_aux_dir)/config.sub \
	$(ac_aux_dir)/compile \
	$(ac_aux_dir)/depcomp \
	$(ac_aux_dir)/install-sh \
	$(ac_aux_dir)/ltconfig \
	$(ac_aux_dir)/ltmain.sh \
	$(ac_aux_dir)/missing \
	$(NULL)

EXTRA_DIST = \
	autogen.sh \
	chewing.pc \
	libchewing.spec \
	Doxyfile \
	$(NULL)

AUTOMAKE_OPTIONS = foreign
SUBDIRS = src/tools data src test

MAINTAINERCLEANFILES = \
	Makefile.in \
	aclocal.m4 \
	configure \
	config.h.in \
	$(AUX_DIST) \
	$(NULL)

DISTCLEANFILES = chewing.pc

CLEANFILES = *.bak 

pkgconfigdir = $(libdir)/pkgconfig

pkgconfig_DATA = chewing.pc

chewing_includedir = $(includedir)/chewing
chewing_include_HEADERS = \
	include/chewingio.h \
	include/mod_aux.h \
	include/chewing.h \
	include/global.h \
	$(NULL)

noinst_HEADERS =\
	include/internal/char-private.h \
	include/internal/chewing-private.h \
	include/internal/chewing-utf8-util.h \
	include/internal/chewingutil.h \
	include/internal/choice-private.h \
	include/internal/dict-private.h \
	include/internal/global-private.h \
	include/internal/hanyupinyin-private.h \
	include/internal/hash-private.h \
	include/internal/key2pho-private.h \
	include/internal/tree-private.h \
	include/internal/userphrase-private.h \
	include/internal/zuin-private.h \
	$(NULL)

installdirs:
	$(mkinstalldirs) $(DESTDIR)$(prefix)/share/man/man3

install-manpages: installdirs
	$(INSTALL_DATA) man/man3/*.3 $(DESTDIR)$(prefix)/share/man/man3
docs:
	if [ -x "@DOXYGEN@" ]; then \
		@DOXYGEN@ Doxyfile; \
	fi
clean-local:
	rm -rf html
	rm -rf man
