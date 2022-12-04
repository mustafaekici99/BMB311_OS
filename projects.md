#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main(int argc, char *argv[])
{
    int num1 = fork();	
    int num2 = fork();	
    int num3 = fork();	
    int num4 = fork();
    int num5 = fork();
    int num6 = fork();
    int num7 = fork();
    int num8 = fork();
    int num9 = fork();
    int num10= fork();

    printf("%d-%d-%d-%d-%d-%d-%d-%d-%d-%d\n", num1, num2, num3, num4, num5, num6, num7, num8, num9, num10);
    
   
   wait(&num1);
    wait(&num2);
    wait(&num3);
    wait(&num4);
    wait(&num5);
    wait(&num6);
    wait(&num7);
    wait(&num8);
    wait(&num9);
    wait(&num10);

    exit(0);
}
