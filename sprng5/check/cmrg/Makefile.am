SUBDIRS = $(FORTRANDIR) .

EXTRA_DIST=cmrg.data .insertlib
INCLUDEDIR = $(top_srcdir)/SRC

LIBDIR=$(top_builddir)/lib
CHKDIR=$(top_srcdir)/check

.NOTPARALLEL:


bin_PROGRAMS = check.ccmrg check_sim.ccmrg time.ccmrg
check_ccmrg_SOURCES = check_gen.cpp
check_ccmrg_DEPENDENCIES = $(LIBDIR)/libsprng.a
check_ccmrg_CXXFLAGS = -I$(INCLUDEDIR)
check_ccmrg_LDADD = -L$(LIBDIR) -lsprng
check_ccmrg_LDFLAGS = 
check_sim_ccmrg_SOURCES = check_gen_simple.cpp
check_sim_ccmrg_DEPENDENCIES = $(LIBDIR)/libsprng.a
check_sim_ccmrg_CXXFLAGS = -I$(INCLUDEDIR)
check_sim_ccmrg_LDADD = -L$(LIBDIR) -lsprng
check_sim_ccmrg_LDFLAGS = 
time_ccmrg_SOURCES = timing.cpp
time_ccmrg_DEPENDENCIES = $(LIBDIR)/libsprng.a
time_ccmrg_LDADD = -L$(LIBDIR) -lsprng
time_ccmrg_CXXFLAGS = -I$(INCLUDEDIR)
time_ccmrg_LDFLAGS = 

bin_SCRIPTS = checkcmrg timecmrg
CLEANFILES = $(bin_SCRIPTS)

checkcmrg: $(CHKDIR)/insertlib
	rm -f ./checkcmrg
	@$(CHKDIR)/insertlib cmrg ./checkcmrg "Checking Default C++ interface:" "check.ccmrg < ./cmrg.data 2> /dev/null" ./check.ccmrg
	@$(CHKDIR)/insertlib cmrg ./checkcmrg "Checking Simple C++ interface:" "check_sim.ccmrg < ./cmrg.data 2> /dev/null" ./check_sim.ccmrg

timecmrg: $(CHKDIR)/insertlib
	rm -f ./timecmrg
	@$(CHKDIR)/insertlib cmrg ./timecmrg "Timing C++ interface" ./time.ccmrg ./time.ccmrg
	chmod u+x ./timecmrg
