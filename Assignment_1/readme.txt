Course Name: COMP5160
Name: Sharmin Sultana
Email: sharmin_sultana@student.uml.edu

Degree of Success: 100%

Approach Strategy:
1.	For return environment, I first initialized the stack size and allocated them to the return environment for each process.

2.	I used the end_game function to initialize the return environment. Here, a stack was allocated for the return environment (rtn_env) of each process.

3.	Makecontext function was used to make a context in the pointer of rtn_env with the function context_switch.

4.	I used uc_link field in the ucontext_t structure which holds the successive context when the current context ends.

5.	The context_switch function calls the signal handler with the signal of ending a process to inform the system that this thread is completed and starts the next context.

Problems: 
Based on my perception, I did not find any problem with this code.
