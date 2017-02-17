#------------------------------------------------------------------------------
# Makefile for building code to test EEC EMU Inteface
#------------------------------------------------------------------------------
SRCDIR = ./benchmarks/
OBJDIR = ./obj/
MPI_BW_OBJ = $(OBJDIR)osu_bw.o $(OBJDIR)osu_pt2pt.o
MPI_STREAM_OBJ = $(OBJDIR)stream.o
BW_TARGET = bw_mpi
STREAM_TARGET = stream
INCLUDES = $(SRCDIR).
LIBRARIES =.
CC =cc
GCC =gcc
MPICFLAGS =  -o3 -c 
MPILFLAGS = -O -DSTREAM_ARRAY_SIZE=20000000
#------------------------------------------------------------------------------

all: $(BW_TARGET) $(STREAM_TARGET) 


$(BW_TARGET): $(MPI_BW_OBJ)
	$(CC) $(MPI_BW_OBJ) $(MPILFLAGS) -o $(BW_TARGET)

$(STREAM_TARGET): $(MPI_STREAM_OBJ)
	$(CC) $(MPI_STREAM_OBJ) $(MPILFLAGS) -o $(STREAM_TARGET)

$(OBJDIR)osu_bw.o : $(SRCDIR)osu_bw.c
	$(CC) $(MPICFLAGS) -I$(INCLUDES) $(SRCDIR)osu_bw.c -o $(OBJDIR)osu_bw.o
	
$(OBJDIR)osu_pt2pt.o : $(SRCDIR)osu_pt2pt.c
	$(CC) $(MPICFLAGS) -I$(INCLUDES) $(SRCDIR)osu_pt2pt.c -o $(OBJDIR)osu_pt2pt.o

$(OBJDIR)stream.o : $(SRCDIR)stream.c
	$(CC) $(MPICFLAGS) -I$(INCLUDES) $(SRCDIR)stream.c -o $(OBJDIR)stream.o

clean:

	rm -f $(OBJDIR)* $(BW_TARGET) $(STREAM_TARGET)
