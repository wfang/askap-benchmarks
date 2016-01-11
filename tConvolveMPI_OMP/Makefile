# Copyright (c) 2009 CSIRO
# Australia Telescope National Facility (ATNF)
# Commonwealth Scientific and Industrial Research Organisation (CSIRO)
# PO Box 76, Epping NSW 1710, Australia
# atnf-enquiries@csiro.au
#
# The ASKAP software distribution is free software: you can redistribute it
# and/or modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of the License,
# or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA
#
#
#MKLROOT=/mkl156

CXX=mpiicc

CFLAGS =-O3  -openmp -I${MKLROOT}/include 
LIBS=-Wl,--start-group ${MKLROOT}/lib/intel64/libmkl_intel_lp64.a ${MKLROOT}/lib/intel64/libmkl_core.a ${MKLROOT}/lib/intel64/libmkl_intel_thread.a ${MKLROOT}/lib/intel64/libmkl_blacs_intelmpi_lp64.a -Wl,--end-group -lpthread -lm



EXENAME = tConvolveMPI_OMP
OBJS = tConvolveMPI_OMP.o Stopwatch.o Benchmark.o

all:		$(EXENAME)

%.o:		%.cc %.h
		$(CXX) $(CFLAGS) -c $<

$(EXENAME):	$(OBJS)
		$(CXX) $(CFLAGS) $(LIBS) -o $(EXENAME) $(OBJS)

clean:
		rm -f $(EXENAME) *.o
