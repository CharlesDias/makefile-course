# target: prerequisites
# 		commands

build: my_lib.o main.o
	@echo "------------------------- Building ------------------------"
	g++ main.o my_lib.o -o main
	@echo ""
	@echo "Done!"

main.o:
	g++ main.cpp -c

my_lib.o:
	g++ my_lib.cpp -c

execute:
	@echo "------------------ Executing the program -----------------"
	@./main

clean:
	@echo "-------------------------- Clean -------------------------"
	@rm -f main *.o