*******************************************************
COMP5160
Assignment 3
*******************************************************
Sharmin Sultana
Sharmin_Sultana@student.uml.edu
*******************************************************

*************************
Degree of Success: 100%
*************************

***This assignment is made on mercury2***

*******************
Approach Strategy:
*******************


1. Design Strategy: Here, we designed the emulated xinu command line interpreter using flex system. The "cs516cli.ll" contains all the command patterns including integer token. Using flex system, this file is converted into a flex scanner named "lex.yy.c". When a user type any command, this file calls the yylex() function to get the token. After that, necessary functionality were added for each of the commands using switch statement. Then the behaviour of the xinu system and functionality of the command interpreter for each command were checked using command input to the Command line interpreter and viewing proc tab after each command.

2. CLI Implimentation: The CLI is designed as a function and has been run as a process in xinu. The CLI contains the following command:

SHOW:	 Following Commands are Valid after Show:
	PROC:	 Show the proc table
	SLP:	 Show the proc in Sleep Queue
	RDY:	 Show the proc in Ready Queue
	CMDS:	 Show all Commands
SUSPEND: Suspend the proc with PID given after this command
RESUME:	 Resume the proc with PID given after this command
KILL:	 Kill the proc with PID given after this command
EXIT:	 Exit CLI and Xinu
CREATE:	 Create a proc. Following Commands are valid after CREATE:
	RCV:	 Create a proc in Recieve state
	SLP:	 Create a proc in Sleep sleep
	WTR:	 Create a proc in wait state
	LOOP:	 Create a proc who run a large loop 

3. Sample Run: A sample execution showing all necessary functionality is given below:

    #
MAIN: main function is alive

MAIN: main function has created procs A B and C

MAIN: main function about to suspend self

A: process A is alive
A: process A is about to wait on a sem
B: process B is alive
B: process B is about to sleep for 2 seconds
C: process C is alive
C: process C is about to sleep for 30 seconds

Command Interpreter Ready

enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State FREE Priority 0

Proc 3 State FREE Priority 0

Proc 4 State FREE Priority 0

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State SLEEPING Priority 20

Proc 8 State SEMWAITING Priority 20

Proc 9 State SUSPENDED Priority 20
.!.!.!#.!.!.!.!.!.!.!
B: process B is awake from sleep, will signal sem

A: process A is awake from sem, will wait for msg

B: process B is again to sleep for 2 seconds

enter cmd> show cmds
CLI commands are: 
SHOW:   Following Commands are Valid after Show:
                PROC:    Show the proc table
                SLP:     Show the proc in Sleep Queue
                RDY:     Show the proc in Ready Queue
                CMDS:    Show all Commands
SUSPEND:        Suspend the proc with PID given after this command
RESUME: Resume the proc with PID given after this command
KILL:   Kill the proc with PID given after this command
EXIT:   Exit CLI and Xinu
CREATE:  Create a proc. Following Commands are valid after CREATE:
                RCV:     Create a proc in Recieve state
                SLP:     Create a proc in Sleep sleep
                WTR:     Create a proc in wait state
                LOOP:    Create a proc who run a large loop
.!.!.!.!.!.!#.!.!.!.!
enter cmd> show rdy

 IN SHOW RDY

 Proc 0 Priority 0
.!.!.!.!.!.!.!.!.!#.!
B: process B is awake from sleep, will send msg to A

A: process A has received a msg, goodbye
<>
B: process B is about to sleep for 2 seconds

enter cmd> 
.!.!.!.!.!.!.!.!.!.!
enter cmd> 

.!.!#.!.!.!.!.!.!.!.!
B: process B is awake from sleep, goodbye
<>
enter cmd> SHOW SLP

 IN SHOW SLP
 Proc 6 Wait Ticks 240
.!.!.!.!.!#.!.!.!.!.!
enter cmd> create rc

 Bad operand after CREATE is rc 
.!.!.!.!.!.!.!.!#.!.!
enter cmd> create slp

 IN CREATE WITH SLP
.!.!.!.!.!.!.!.!.!.!
enter cmd> resume 4

 IN RESUME with PID 4
SLP:    sleep proc is alive with pid 4
SLP:    sleep will to sleep for 120 seconds
.!#.!.!.!.!.!.!.!.!.!
enter cmd> show slp

 IN SHOW SLP
 Proc 6 Wait Ticks 200

 Proc 4 Wait Ticks 990
.!.!.!.!#.!.!.!.!.!.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State FREE Priority 0

Proc 3 State FREE Priority 0

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State SUSPENDED Priority 20
.!.!.!.!.!.!.!.!#.!.!
enter cmd> create rcv

 IN CREATE WITH RCV
.!.!.!.!.!.!.!.!.!.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State FREE Priority 0

Proc 3 State SUSPENDED Priority 15

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State SUSPENDED Priority 20
.!#.!.!.!.!.!.!.!.!.!
enter cmd> resume 3

 IN RESUME with PID 3
RCV proc is alive with pid 3
.!.!.!.!#.!.!.!.!.!.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State FREE Priority 0

Proc 3 State RECVWAITING Priority 15

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State SUSPENDED Priority 20
.!.!.!.!.!.!.!#.!.!.!
enter cmd> create wtr

 IN CREATE WITH WTR
.!.!.!.!.!.!.!.!.!.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State SUSPENDED Priority 15

Proc 3 State RECVWAITING Priority 15

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State SUSPENDED Priority 20
#.!.!.!.!.!.!.!.!.!.!
enter cmd> resume 2

 IN RESUME with PID 2
WTR proc is alive with pid 2
WTR will now wait on semophore 48
.!.!.!#.!.!.!.!.!.!.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State SEMWAITING Priority 15

Proc 3 State RECVWAITING Priority 15

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State SUSPENDED Priority 20
.!.!.!.!.!.!#.!.!.!.!
enter cmd> kill 9

 IN KILL with PID 9 
.!.!.!.!.!.!.!.!.!#.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State SEMWAITING Priority 15

Proc 3 State RECVWAITING Priority 15

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State FREE Priority 20
.!.!.!.!.!.!.!.!.!.!
enter cmd> show slp

 IN SHOW SLP
 Proc 6 Wait Ticks 80

 Proc 4 Wait Ticks 990
.!.!.!#.!.!.!.!.!.!.!
enter cmd> show proc

 IN SHOW PROC

Proc 0 State READY Priority 0

Proc 1 State FREE Priority 0

Proc 2 State SEMWAITING Priority 15

Proc 3 State RECVWAITING Priority 15

Proc 4 State SLEEPING Priority 15

Proc 5 State CURRENT Priority 19

Proc 6 State SLEEPING Priority 20

Proc 7 State FREE Priority 20

Proc 8 State FREE Priority 20

Proc 9 State FREE Priority 20
.!.!.!.!.!.!#.!.!.!.!
enter cmd> exit


Problems:

There is no problem with my solution as far as I concern.
