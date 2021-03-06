### RtAudio tests Makefile - for various flavors of unix

PROGRAMS = info play_saw record_raw in_out play_raw twostreams call_saw call_inout
RM = /bin/rm
SRC_PATH = ../
INCLUDE = ../
OBJECT_PATH = Release
vpath %.o $(OBJECT_PATH)

OBJECTS	=	RtAudio.o

CC       = g++
DEFS     = 
DEFS    += -D__MACOSX_CORE__
CFLAGS   = -O2
CFLAGS  += -Wall -I$(INCLUDE)
LIBRARY  = -lpthread 
LIBRARY += -framework CoreAudio

%.o : $(SRC_PATH)/%.cpp
	$(CC) $(CFLAGS) $(DEFS) -c $(<) -o $(OBJECT_PATH)/$@

all : $(PROGRAMS)

info : info.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o info info.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

play_saw : play_saw.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o play_saw play_saw.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

play_raw : play_raw.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o play_raw play_raw.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

record_raw : record_raw.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o record_raw record_raw.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

in_out : in_out.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o in_out in_out.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

twostreams : twostreams.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o twostreams twostreams.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

call_saw : call_saw.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o call_saw call_saw.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

call_inout : call_inout.cpp $(OBJECTS)
	$(CC) $(CFLAGS) $(DEFS) -o call_inout call_inout.cpp $(OBJECT_PATH)/RtAudio.o $(LIBRARY)

clean : 
	-rm $(OBJECT_PATH)/*.o
	-rm $(PROGRAMS)
	-rm -f *~

strip : 
	strip $(PROGRAMS)
