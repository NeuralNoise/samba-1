# simple makefile wrapper to run waf

WAF=WAF_MAKE=1 PATH=buildtools/bin:../buildtools/bin:$$PATH waf

all:
	$(WAF) build

install:
	$(WAF) install

uninstall:
	$(WAF) uninstall

test: FORCE
	$(WAF) test $(TEST_OPTIONS)

testenv:
	$(WAF) test --testenv $(TEST_OPTIONS)

autotest:
	$(WAF) autotest $(TEST_OPTIONS)

quicktest:
	$(WAF) test --quick $(TEST_OPTIONS)

show_version:
	@touch .tmplock
	@WAFLOCK=.tmplock $(WAF) show_version

dist:
	touch .tmplock
	WAFLOCK=.tmplock $(WAF) dist

distcheck:
	touch .tmplock
	WAFLOCK=.tmplock $(WAF) distcheck

rpm:
	touch .tmplock
	WAFLOCK=.tmplock $(WAF) rpm

clean:
	$(WAF) clean

distclean:
	$(WAF) distclean

reconfigure: configure
	$(WAF) reconfigure

show_waf_options:
	$(WAF) --help

# some compatibility make targets
everything: all

testsuite: all

check: test

torture: all

# this should do an install as well, once install is finished
installcheck: test

etags:
	$(WAF) etags

ctags:
	touch .tmplock
	WAFLOCK=.tmplock $(WAF) ctags

pydoctor:
	$(WAF) pydoctor

bin/%:: FORCE
	$(WAF) --targets=`basename $@`
FORCE:
