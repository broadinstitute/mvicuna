PROG=../bin/mvicuna

#COMPILER=/opt/local/bin/g++
# server 
#COMPILER=/broad/software/free/Linux/redhat_5_x86_64/pkgs/gcc_4.7.2/bin/g++ 
COMPILER=g++
FLAGs=-std=c++0x
OMP=-fopenmp

all:
	mkdir -p `dirname $(PROG)`
	$(COMPILER) $(FLAGs) -O3 *.cpp -o $(PROG)
	
clean:
	rm -rf $(PROG)
