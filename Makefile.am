## automake Makefile for FSMegaInfo

ACLOCAL_AMFLAGS = -I m4 --install

bin_PROGRAMS = FSMegaInfo

FSMegaInfo_SOURCES = AliasManager.c BSD.c BSD.h BSDAttrList.c Command.c Command.h DiskArb.c FieldPrinter.c FieldPrinter.h FileManager.c FolderManager.c FSMegaInfo.c

#TODO: check that these flags are supported:
AM_WARNFLAGS = -Wmissing-prototypes -Wreturn-type -Wmissing-braces \
	       -Wparentheses -Wswitch -Wunused-parameter \
	       -Wunused-variable -Wunused-value -Wunknown-pragmas \
	       -Wshadow -Wall -Wimplicit -Wextra -Wfloat-equal \
	       -Wpointer-arith -Wstrict-prototypes -Wold-style-definition
PASCAL_STRINGS_FLAG = -fpascal-strings
FSMegaInfo_CFLAGS = -mfix-and-continue -mmacosx-version-min=10.4 $(AM_WARNFLAGS) # $(PASCAL_STRINGS_FLAG)
# No need to repeat the version-min flag in here; it already gets brought
# in by the CFLAGS:
FSMegaInfo_LDFLAGS = -framework CoreServices -framework DiskArbitration
if HAVE_CORRECT_SYSROOT
FSMegaInfo_CPPFLAGS = -isysroot /Developer/SDKs/MacOSX10.5.sdk
FSMegaInfo_LDFLAGS += -isysroot /Developer/SDKs/MacOSX10.5.sdk
endif
## (end HAVE_CORRECT_SYSROOT)

noinst_HEADERS = BSD.h Command.h FieldPrinter.h

SUBDIRS = . Tests

DISTCLEANFILES = *~ autoscan.log .DS_Store

MAINTAINERCLEANFILES = configure.scan

configure.scan:
	autoscan || touch configure.scan

distclean-local:
	rm -f @PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz
	rm -rf autom4te.cache || rmdir autom4te.cache
	-rm -rf *.dSYM || rmdir *.dSYM
