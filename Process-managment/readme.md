### Process Basics:

- **Process ID (PID):**
  - A unique identifier assigned to each process.
  - Keeps track of processes in the system.
  - No two processes share the same PID.

- **Process Initialization:**
  - When a command is executed, a new process is created.
  - Each process has a unique PID assigned by the system.

### Running Processes:

- **Foreground Process:**
  - Default mode where a process runs, receiving input from the keyboard and sending output to the screen.
  - May cause a delay in running other processes until completion.

- **Background Process:**
  - Runs in the background without keyboard input.
  - Allows parallel execution of other processes.
  - Indicated by appending `&` to the command.

### Tracking Processes:

- **ps (Process Status):**
  - Lists running processes.
  - `ps` or `ps -f` for detailed information.
  - Displays PID, CPU utilization, start time, terminal type, and more.

    ps [-aefls] [-u UID] [-p PID]

    Report process status

     -a, --all       show processes of all users
     -e, --everyone  show processes of all users
     -f, --full      show process uids, ppids
     -h, --help      output usage information and exit
     -l, --long      show process uids, ppids, pgids, winpids
     -p, --process   show information for specified PID
     -s, --summary   show process summary
     -u, --user      list processes owned by UID
     -V, --version   output version information and exit
     -W, --windows   show windows as well as cygwin processes
    With no options, ps outputs the long format by default


- **Stopping a Process:**
  - `Ctrl + c` for foreground processes.
  - `kill` command for background processes (e.g., `kill 19`).
  - Use `kill -9` if a process doesn't respond to a regular kill.

### Other Process Commands:

- **bg:**
  - Resumes suspended jobs in the background (`bg %19`).

- **fg:**
  - Continues a stopped job by running it in the foreground (`fg 19`).

- **top:**
  - Displays all running processes in the Linux environment.

- **nice and renice:**
  - `nice` starts a new process with a specified priority.
  - `renice` changes the priority of an already running process.

- **df:**
  - Shows disk space usage for file systems (`df`).

- **free:**
  - Displays total, used, and free physical and swap memory.

### Types of Processes:

- **Parent and Child Processes:**
  - Parent processes spawn child processes.
  - Columns in `ps -f` show process ID and parent's process ID.

- **Zombie and Orphan Processes:**
  - Orphan processes result from a parent process being killed.
  - Zombie processes are terminated but still listed in the process table.

- **Daemon Processes:**
  - System-related background processes.
  - Often run with root permissions.
  - Examples include print daemons.
  - Displayed with '?' in the tty field when using `ps -ef`.


### Process Management in Linux

A process in Linux represents a program in execution. There are two main types of processes: Foreground and Background.

#### Types of Processes:

1. **Foreground Processes:**
   - Also known as interactive processes.
   - Initiated by the user or programmer, taking input and returning output.
   - Prevents the initiation of new processes from the same terminal while running.

2. **Background Processes:**
   - Also known as non-interactive processes.
   - Initiated by the system or users, can be managed by users.
   - Has a unique PID and allows the initiation of other processes from the same terminal.

#### Practical Process Management:

1. **Example of Foreground Process:**
   - Command: `sleep 5`
   - Executes and allows the initiation of another command in the same terminal.

2. **Stopping a Process:**
   - Command: `sleep 100`
   - Pressing `CTRL+Z` in between execution stops the process.

3. **List of Jobs:**
   - Command: `jobs`
   - Displays running, stopped, and pending processes.

4. **Run Pending and Force Stopped Jobs in Background:**
   - Command: `bg`
   - Starts stopped and pending processes in the background.

5. **Details of a Process in Background:**
   - Command: `ps -ef | grep sleep`
   - Retrieves details of a background process.

6. **Run Pending and Force Stopped Jobs in Foreground:**
   - Command: `fg`
   - Starts stopped and pending processes in the foreground.

7. **Run a Process in Background (nohup):**
   - Command: `nohup sleep 100 &`
   - Runs a process in the background, unaffected by terminal closure.

8. **Run Processes in Background Directly:**
   - Command: `sleep 100 &`
   - Runs a process in the background, displaying the process ID.

9. **Run Processes with Priority:**
   - Command: `nice -n 5 sleep 100`
   - Sets process priority (here, 5), balancing system impact.

10. **List of Running Processes:**
    - Command: `top`
    - Displays all running processes on the Linux machine.


### Process States and Transitions 

#### Process States:

1. **User-Running:**
   - The process is currently executing in user mode.
   - Represents a user process operating in user mode.

2. **Kernel-Running:**
   - The process is currently executing in kernel mode.
   - Indicates a kernel process running in kernel mode.

3. **Ready to Run in Memory:**
   - The process is not executing but is ready to run as soon as the scheduler chooses it.
   - Multiple processes may be in this state, and the scheduling algorithm determines the next process to execute.

4. **Asleep in Memory:**
   - The process is sleeping but resides in main memory.
   - It is waiting for a task to begin and is in a blocked state.

5. **Ready to Run, Swapped:**
   - The process is ready to run and can be swapped by the processor into main memory.
   - Awaiting scheduling by the kernel for execution.

6. **Sleep, Swapped:**
   - The process has been swapped to secondary storage and is in a blocked state.
   - It makes space for the execution of other processes in main memory and may resume once the task is fulfilled.

7. **Preempted:**
   - The kernel preempts an ongoing process to allocate resources to another process.
   - The preempted process moves from the kernel to user mode.

8. **Created:**
   - The process is newly created but not yet running.
   - The initial state for all processes.

9. **Zombie:**
   - The process has been thoroughly executed, and the exit call has been enabled.
   - The process no longer exists but retains a statistical record.
   - The final state of all processes.

#### Process Transitions:

1. **User-Running → Kernel-Running:**
   - Process transitions to kernel mode for kernel-related operations.

2. **Kernel-Running → Ready to Run in Memory:**
   - After kernel processing, the process is rescheduled to the kernel and is ready to run in memory.

3. **Ready to Run in Memory → Asleep in Memory:**
   - The process is sleeping but resides in main memory, awaiting a task.

4. **Asleep in Memory → Ready to Run, Swapped:**
   - The process is ready to run and can be swapped into main memory.

5. **Ready to Run, Swapped → Sleep, Swapped:**
   - The process has been swapped to secondary storage, making space in main memory.

6. **Sleep, Swapped → Preempted:**
   - The kernel preempts an ongoing process, transitioning from kernel to user mode.

7. **Preempted → Created:**
   - A new process is created and enters the system.

8. **Created → Zombie:**
   - The process has completed its execution and becomes a zombie, retaining statistical information.