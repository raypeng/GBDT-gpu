#CXXFLAGS='-std=c++11 -MMD -MP'

TARGET = main
OBJS = main.o decision_tree.o dataset.o mpi_util.o bindist.o util.o heap.o
DFILES = main.d decision_tree.d dataset.d mpi_util.d bindist.d util.d heap.d

CC = mpic++
CXXFLAGS = -std=c++11 -fopenmp -g -O3 -I/opt/openmpi/include/ -Wl,-rpath,/opt/gcc/4.9.2/lib64

CXXFLAGS += -MMD -MP
LDFLAGS += $(LIBS)

CC2 = g++
CXXFLAGS2 = -std=c++11 -g -O3
TARGET2 = local

default:	$(TARGET)
all:		$(TARGET)

$(TARGET):	$(OBJS)
	$(CC) $(CXXFLAGS) -o $@ $^ $(LDFLAGS)

$(TARGET2): $(OBJS)
	$(CC2) $(2CXXFLAGS) -o $@ $^ $(LDFLAGS)



%.o: %.c
	$(CC) $(CXXFLAGS) -c -o $@ $<

DEPS = $(OBJS:%.o=%.d)
-include $(DEPS)

clean:
	rm -f $(OBJS) $(DFILES) latedays.qsub.* main *~
