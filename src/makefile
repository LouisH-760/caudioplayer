CC=gcc -std=c99 -c
CL=gcc -g -o audioplayer
LDFLAGS=-lavformat -lavcodec -lavutil -lswscale -lswresample -lpthread -lz -lm -lva -llzma
# hardcoded SDL flags, because `sdl-config --libs --cflags` does not work, somehow
SDLFLAGS=-L/usr/lib/x86_64-linux-gnu -lSDL -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT

all:audioplayer

audioplayer:audioplayer.o audiochunk.o main.o
	$(info linking)
	$(CL) main.o audiochunk.o audioplayer.o $(LDFLAGS) $(SDLFLAGS)
	$(info remving object files)
	rm *.o

audioplayer.o:
	$(info Compiling audioplayer.c)
	$(warning using -Wno-deprecated-declarations!)
	$(CC) -c audioplayer.c -Wno-deprecated-declarations

main.o:
	$(info Compiling main.c)
	$(CC) -c main.c

audiochunk.o:
	$(info Compiling audiochunk.c)
	$(CC) -c audiochunk.c

clean:
	$(info removing executable)
	rm audioplayer
