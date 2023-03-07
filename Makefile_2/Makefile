all: main.o print_lib.o
	g++ -std=c++20 main.o print_lib.o -o main

main.o:
	g++ -std=c++20 main.cpp -c

print_lib.o:
	g++ -std=c++20 print_lib.cpp -c

clean:
	rm *.o main