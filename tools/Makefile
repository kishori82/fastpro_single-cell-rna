
CC = g++ -std=c++17 -fPIC  -DHTSLIB -Wall -O4  -Wwrite-strings 
CFLAGS = -IlibStatGen/include -Ihtslib-1.13  -Igzstream -Lhtslib-1.13 -LlibStatGen  -Lgzstream
LIBS = -lStatGen -lz -lpthread -lstdc++fs -lgzstream -lhts

TARGET1 = fastqprocess
TARGET2 = TagSort

SUBDIRS := libStatGen gzstream htslib-1.13 src

.PHONY: all clean $(SUBDIRS)
all: $(SUBDIRS) $(TARGET2) $(TARGET1)

$(SUBDIRS):
	$(MAKE) -C $@

OBJ =  htslib_tagsort.o globals.o sort_write.o metricgatherer.o utilities.o input_options.o 

#install: $(TARGET1) $(TARGET2)
#	cp $(TARGET1) ../bin/
#	cp $(TARGET2) ../bin/
#	cp ../htslib-1.13/*.so.? ../bin/


$(TARGET1):  src/fastqprocess.o src/utilities.o src/sort_write.o src/metricgatherer.o src/input_options.o src/globals.o
	$(CC) -o $@ $^ $(CFLAGS)  $(LIBS) 

$(TARGET2): src/tagsort.o src/htslib_tagsort.o src/globals.o src/utilities.o src/sort_write.o src/metricgatherer.o src/input_options.o
	$(CC) -Wl,-rpath,/usr/local/bin:bin:. -o $@ $^ $(CFLAGS) $(LIBS) 

.PHONY: clean
clean:
	rm -f *.o *~ core $(INCDIR)/*~  *.o *.so *.a
	rm -rf $(TARGET1) $(TARGET2)
        
        # clean the subdirs
	for dir in $(SUBDIRS); do \
		$(MAKE) -C $$dir clean; \
	done

