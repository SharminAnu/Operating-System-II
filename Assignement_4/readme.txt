COMP5160
Assignment 4
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
1. In this assignment, we replace the XINU read and write routines and construct a sparate serial port hardware emulation process which used a shared memory segment. It reads and writes from the Xinu system's 16-bit csr registers using the shared memory section.
2. Then this shared memory segments are used to imitate the csr register from the xinu end, which is where the output character is written and the input character is interpreted.
3. For the xinu terminal emulation process, we have used Unix system interrupts 10, 12 as input and output interrupts. 
4. We applied the address of the shared memory segment to the csr address of the tty device in the init function during tty device initialization. 
5. In addition, we modified the input and output interrupt routines to emulate the hardware clearing of interrupts.

Conclusion: 
There was no problem with the code as far as I know.
