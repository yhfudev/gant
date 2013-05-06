# Author: Yunhui Fu <yhfudev@gmail.com>
# Lincense: GPL v3.0

if ENABLE_DOXYGEN_DOC

all-local: doxygen.stamp

doxygen.stamp: $(to $(top_srcdir)/src/*.c $(top_srcdir)/src/*.cc $(top_srcdir)/src/*.h $(top_srcdir)/include/*.h
	$(DOXYGEN)
	touch doxygen.stamp

install-data-local: install-html

install-html:
	$(INSTALL) -d $(DESTDIR)$(htmldocdir)
	$(INSTALL_DATA) html/* $(DESTDIR)$(htmldocdir)

uninstall-local:
	rm -rf $(DESTDIR)$(htmldocdir)

clean-local:
	rm -rf html man
	rm -f doxygen.stamp

else

install-data-local:
uninstall-local:
clean-local:

endif

