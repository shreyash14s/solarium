#
# Makefile for the Solar System Simulator project (BarnesHut version with OpenMP and MPI)
#

CC=mpicc
CFLAGS=-c -std=c99 -D_XOPEN_SOURCE=600 -O2 -fopenmp -I../Common -I../../Spica/C
LD=mpicc
LDFLAGS=-fopenmp
SOURCES=main.c Object.c Octree.c
OBJECTS=$(SOURCES:.c=.o)
EXECUTABLE=BarnesHut

%.o:	%.c
	$(CC) $(CFLAGS) $< -o $@

$(EXECUTABLE):	$(OBJECTS)
	$(LD) $(LDFLAGS) $(OBJECTS) -L../Common -L../../Spica/C -lCommon -lSpicaC -lm -o $@

# File Dependencies
###################

main.o:		main.c ../Common/global.h ../Common/Initialize.h

Object.o:	Object.c ../Common/global.h Octree.h

Octree.o:	Octree.c Octree.h

# Additional Rules
##################
clean:
	rm -f *.o *.bc *.s *.ll *~ $(EXECUTABLE)
