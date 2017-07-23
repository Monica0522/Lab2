# Lab2
Lab 2, forking and waiting
//  Monica Andrade
//  Comp 322
//  lab2
//
//  Created by Monica Andrade on 7/20/17.
//  Copyright © 2017 Monica Andrade. All rights reserved.
//

#include <unistd.h>
#include <sys/types.h>
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include <sys/wait.h>


int main(int argc, char * argv[]) {
    
    pid_t pid;
    int i;
   
    for(i = 1; i <argc; i++)
    {
        pid = fork();
        
        if(pid > 0)
        {
            printf("Filename: %s\tPID: %d\n", argv[i], getpid());
            exit(1);
        }
        else if (pid ==0){
            printf("Filename: %s\tPID: %d\n", argv[i], getpid());
            exit(1);
        }
        else
        {
            pid = wait(NULL);
        }
    }
    system("ps -H");
    printf("Done!\n");
    
    return 0;
}
