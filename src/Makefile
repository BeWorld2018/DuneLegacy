TARGET = dunelegacy
LIBS =  -lSDL2  -L/gg/usr/local/lib -noixemul -lc  -lc -lm -lwstdio -lSDL2_mixer -lSDL2_ttf 
CXX = ppc-morphos-g++-9
STRIP = strip
CXXFLAGS = -I/gg/usr/local/include -noixemul -O2 -Wall -I/gg/usr/local/include/SDL2 -I../include -I. -I../ -fexceptions -Wextra
#-fpermissive

.PHONY: default all clean

default: $(TARGET)
all: default

HEADERS = $(wildcard *.h)
OBJS = $(patsubst %.cpp, %.o, $(wildcard *.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard units/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard CutScenes/*.cpp))
OBJS += $(patsubst %.c, %.o, $(wildcard enet/*.c))
OBJS += $(patsubst %.cpp, %.o, $(wildcard FileClasses/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard FileClasses/adl/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard FileClasses/music/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard FileClasses/xmidi/*.cpp))
OBJS += $(patsubst %.c, %.o, $(wildcard fixmath/*.c))
OBJS += $(patsubst %.cpp, %.o, $(wildcard GUI/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard GUI/dune/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard INIMap/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard MapEditor/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard Menu/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard misc/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard Network/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard player/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard structures/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard Trigger/*.cpp))
OBJS += $(patsubst %.cpp, %.o, $(wildcard players/*.cpp))

%.o: %.c $(HEADERS)
	$(CXX) $(CXXFLAGS) -c $< -o $@

.PRECIOUS: $(TARGET) $(OBJS)

$(TARGET): $(OBJS)
	$(CXX) $(OBJS) $(LIBS) -o $@
	$(STRIP) --strip-all $(TARGET) -o $(TARGET).pak
	
clean:
	rm -f *.o
	rm -f $(TARGET)

dump:
	objdump --disassemble-all --reloc $(TARGET) >$(TARGET).s