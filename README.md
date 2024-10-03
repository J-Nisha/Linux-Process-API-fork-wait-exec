# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```
## OUTPUT
![371402674-d4a54287-81dd-4841-b053-7dfd409d796b](https://github.com/user-attachments/assets/84c66a96-17ef-4ae9-a7d9-1ee40887d9bf)
![371402837-d8f838ac-1fd3-4191-9fc7-5af675344eaa](https://github.com/user-attachments/assets/a5788076-c5ff-46fc-aaf9-a7a710586bd9)


## C Program to create new process using Linux API system calls fork() and exit()
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
int main() {
    int pid;
    pid = fork();
    if (pid == -1) {
        perror("fork");
        exit(EXIT_FAILURE);
    }
    else if (pid == 0) {
        printf("I am child, my pid is %d\n", getpid());
        printf("My parent pid is: %d\n", getppid());
        exit(EXIT_SUCCESS);
    }
    else {
        printf("I am parent, my pid is %d\n", getpid());
        sleep(100);
        exit(EXIT_SUCCESS);
    }
    return 0;
}
```
## OUTPUT
![371402977-509bf362-cc6d-481d-beeb-d5c6a322d3a5](https://github.com/user-attachments/assets/1db6e18b-42de-43cc-b8a8-40f35976451d)
![371403033-cc71d2cc-dbf2-479a-ac29-c95e67b89052](https://github.com/user-attachments/assets/16af06cf-3cb1-4943-8852-5aa352843262)


## C Program to execute Linux system commands using Linux API system calls exec() family
```
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);
}

```

## OUTPUT
![371403246-6731672a-2a34-4fdc-a2c3-d0c0f78e0320](https://github.com/user-attachments/assets/9e61f88a-bbc4-45b3-b6ea-a0c7976212c1)
![371403316-27fdc194-a62d-4a3b-bdd7-0defce98b7df](https://github.com/user-attachments/assets/9746cdfc-282c-42dd-ab20-eeb1afb22857)

## RESULT:
The programs are executed successfully.
