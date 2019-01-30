LIB_RK_IQ=librkisp.so

all:
	cp $(top_srcdir)/gst-libs/rkisp/$(target_cpu)/$(LIB_RK_IQ) \
		$(top_srcdir)/gst-libs/rkisp/$(LIB_RK_IQ)

install-data-am:
	echo " $(MKDIR_P) '$(DESTDIR)$(libdir)'"; \
	$(MKDIR_P) "$(DESTDIR)$(libdir)" || exit 1; \
	install -m 0644 $(top_srcdir)/gst-libs/rkisp/$(LIB_RK_IQ) $(DESTDIR)$(libdir)/$(LIB_RK_IQ)