COMPLR = g++
CFLAGS = -Wall -Wextra -g
SRCDIR = lib
INCDIR = header
BINDIR = bin
TARGET = Lambda
DEPEND = 

SOURCES := main.cpp $(wildcard $(SRCDIR)/*.cpp) $(wildcard *.cpp)
HEADERS := $(wildcard $(INCDIR)/*.h) $(wildcard $(INCDIR)/*.hpp) $(wildcard  *.h) $(wildcard *.hpp)
OBJECTS := $(SOURCES:.cpp=.o)

all:
	@make clean
	@make $(BINDIR)/$(TARGET)

build:
	@make $(BINDIR)/$(TARGET)

debug:
	@make
	@make debug

full:
	@make
	@make run

$(BINDIR)/$(TARGET): $(OBJECTS)
	@mkdir $(BINDIR)
	$(COMPLR) $(CFLAGS) -I$(INCDIR) $^ -o $@ $(DEPEND)
	@echo "Executible created: $(BINDIR)\$(TARGET).exe"

%.o: %.cpp $(HEADERS)
	@$(COMPLR) $(CFLAGS) -I$(INCDIR) -c $< -o $@ $(DEPEND)

run:
	@.\$(BINDIR)\$(TARGET).exe

debug:
	@gdb .\$(BINDIR)\$(TARGET)

clean:
	@del "$(SRCDIR)\*.o"
	@del "*.o"
	@rd /s /q "$(BINDIR)"
	@echo "Cleaned up the mess."

.PHONY: clean