EIGENDIR     = /usr/include/eigen3/
CC = g++
MPCC = g++
OPENMP = -fopenmp
CFLAGS = -std=c++11 -O3 -I$(EIGENDIR) -fopenmp
LIBS = -m64 -fPIC -fno-strict-aliasing -fexceptions -fopenmp -DNDEBUG -DIL_STD -lm -lpthread -ldl
TARGETS = Cell2Fire

all:	$(TARGETS)
Cell2Fire: Cell2Fire.o CellsFBP.o FuelModel.o SpottingFBP.o ReadCSV.o ReadArgs.o Lightning.o WriteCSV.o Ellipse.o
	$(CC) -o $@ $(LIBS) Cell2Fire.o CellsFBP.o FuelModel.o SpottingFBP.o ReadCSV.o ReadArgs.o Lightning.o WriteCSV.o Ellipse.o
Cell2Fire.o: Cell2Fire.cpp CellsFBP.o FuelModel.o SpottingFBP.o ReadCSV.o ReadArgs.o WriteCSV.o
	$(CC) -c $(CFLAGS) Cell2Fire.cpp
SpottingFBP.o: SpottingFBP.cpp SpottingFBP.h CellsFBP.h
	$(CC) -c $(CFLAGS) SpottingFBP.cpp CellsFBP.h

CellsFBP.o: CellsFBP.cpp CellsFBP.h FuelModel.o
	$(CC) -c $(CFLAGS) CellsFBP.cpp
ReadCSV.o: ReadCSV.cpp ReadCSV.h 
	$(CC) -c $(CFLAGS) ReadCSV.cpp
ReadArgs.o: ReadArgs.cpp ReadArgs.h
	$(CC) -c $(CFLAGS) ReadArgs.cpp
Lightning.o: Lightning.cpp Lightning.h
	$(CC) -c $(CFLAGS) Lightning.cpp
Forest.o: Forest.cpp Forest.h
	$(CC) -c $(CFLAGS) Forest.cpp
WriteCSV.o: WriteCSV.cpp WriteCSV.h
	$(CC) -c $(CFLAGS) WriteCSV.cpp
Ellipse.o: Ellipse.cpp Ellipse.h 
	$(CC) -c $(LIBS) $(CFLAGS) Ellipse.cpp 
FuelModel.o: FuelModel.cpp FuelModel.h
	$(CC) -c $(LIBS) $(CFLAGS) FuelModel.cpp 
clean:
	rm Lightning.o ReadArgs.o ReadCSV.o Cell2Fire.o CellsFBP.o Cell2Fire SpottingFBP.o Forest.o WriteCSV.o Ellipse.o FuelModel.o *.gch
