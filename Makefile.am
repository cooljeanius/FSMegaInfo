## automake Makefile for FSMegaInfo

ACLOCAL_AMFLAGS = -I m4 --install

bin_PROGRAMS = FSMegaInfo

FSMegaInfo_SOURCES = AliasManager.c BSD.c BSD.h BSDAttrList.c Command.c Command.h DiskArb.c FieldPrinter.c FieldPrinter.h FileManager.c FolderManager.c FSMegaInfo.c

#TODO: check that these flags are supported:
FSMegaInfo_CFLAGS = -fpascal-strings -mfix-and-continue -mmacosx-version-min=10.4
FSMegaInfo_CPPFLAGS = -isysroot /Developer/SDKs/MacOSX10.5.sdk
# No need to repeat the version-min flag in here; it already gets brought
# in by the CFLAGS:
FSMegaInfo_LDFLAGS = -isysroot /Developer/SDKs/MacOSX10.5.sdk -framework CoreServices -framework DiskArbitration

noinst_HEADERS = BSD.h Command.h FieldPrinter.h

SUBDIRS = Tests

DISTCLEANFILES = *~ autoscan.log .DS_Store

MAINTAINERCLEANFILES = configure.scan

configure.scan:
	autoscan || touch configure.scan

distclean-local:
	rm -f @PACKAGE_TARNAME@-@PACKAGE_VERSION@.tar.gz
	rm -rf autom4te.cache || rmdir autom4te.cache
