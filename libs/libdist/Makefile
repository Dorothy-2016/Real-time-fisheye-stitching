.PHONY: all release clean debug
TARGET := libdist.a
CXXFLAGS += -I ./include
CXXFLAGS += -O3 -fopenmp -Wall -Wextra -march=native  -msse2 -msse3
# -Werror
objects := $(patsubst %.cpp, %.o, $(wildcard src/*.cpp))

all : release

$(TARGET):$(objects)
	if [ ! -d lib ] ; then mkdir lib ; fi
	ar rs ./lib/$@ $^

release : $(objects) $(TARGET)
release : CXXFLAGS += -DNDEBUG

debug : $(objects) $(TARGET)
debug : CXXFLAGS += -DDEBUG -g

clean:
	rm -rf ./lib $(objects)
