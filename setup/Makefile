# Copyright (c) 2006 Red Hat, Inc. All rights reserved. This copyrighted material 
# is made available to anyone wishing to use, modify, copy, or
# redistribute it subject to the terms and conditions of the GNU General
# Public License v.2.
#
# This program is distributed in the hope that it will be useful, but WITHOUT ANY
# WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
# PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
#
# Author: Bill Peck <bpeck@redhat.com>

# The toplevel namespace within which the test lives.
# FIXME: You will need to change this:
TOPLEVEL_NAMESPACE=distribution

# The name of the package under test:
# FIXME: you wil need to change this:
PACKAGE_NAME=beaker

# The path of the test below the package:
# FIXME: you wil need to change this:
RELATIVE_PATH=setup

# Version of the Test. Used with make tag.
export TESTVERSION=1.4.3

# The combined namespace of the test.
export TEST=/$(TOPLEVEL_NAMESPACE)/$(PACKAGE_NAME)/$(RELATIVE_PATH)


# A phony target is one that is not really the name of a file.
# It is just a name for some commands to be executed when you
# make an explicit request. There are two reasons to use a
# phony target: to avoid a conflict with a file of the same
# name, and to improve performance.
.PHONY: all install download clean

# executables to be built should be added here, they will be generated on the system under test.
BUILT_FILES= 

# data files, .c files, scripts anything needed to either compile the test and/or run it.
FILES=$(METADATA) runtest.sh Makefile PURPOSE

run: $(FILES) build
	./runtest.sh

build: $(BUILT_FILES)
	chmod a+x ./runtest.sh

clean:
	rm -f *~ *.rpm $(BUILT_FILES)

# You may need to add other targets e.g. to build executables from source code
# Add them here:


# Include Common Makefile
include /usr/share/rhts/lib/rhts-make.include

# Generate the testinfo.desc here:
$(METADATA): Makefile
	@touch $(METADATA)
# Change to the test owner's name
	@echo "Owner:        Bill Peck <bpeck@redhat.com>" > $(METADATA)
	@echo "Name:         $(TEST)" >> $(METADATA)
	@echo "Path:         $(TEST_DIR)"	>> $(METADATA)
	@echo "License:      GPLv2" >> $(METADATA)
	@echo "TestVersion:  $(TESTVERSION)"	>> $(METADATA)
	@echo "Description:  Sanity test for beaker ">> $(METADATA)
	@echo "TestTime:     4h" >> $(METADATA)
	@echo "Requires:     beakerlib" >> $(METADATA)
	@echo "Requires:     mysql-server" >> $(METADATA)
	@echo "Requires:     rh-mariadb102" >> $(METADATA)
	@echo "Requires:     rh-mariadb102-mariadb-syspaths" >> $(METADATA)
	@echo "Requires:     MySQL-python" >> $(METADATA)
	@echo "Requires:     python2-mysql" >> $(METADATA)
	@echo "Requires:     tftp-server" >> $(METADATA)
	@echo "Requires:     autofs" >> $(METADATA)
	@echo "Requires:     curl" >> $(METADATA)
	@echo "Requires:     yum-utils" >> $(METADATA)

