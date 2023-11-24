### Unix/Linux - Processes Management

In Unix/Linux, process management is crucial for executing and controlling programs. Processes, identified by unique process IDs (pids), can run in the foreground or background.

#### Starting a Process

1. **Foreground Processes:**
   - Default mode; interacts with the user.
   - Accepts input from the keyboard and sends output to the screen.
   - Commands run without an ampersand (&) in the foreground.

   ```bash
   $ ls ch*.doc
   ```

2. **Background Processes:**
   - Runs independently without a direct connection to the keyboard.
   - Allows running other commands simultaneously.
   - Add an ampersand (&) at the end of the command.

   ```bash
   $ ls ch*.doc &
   ```

   View background process information:

   ```bash
   [1]   +   Done                 ls ch*.doc &
   ```

#### Listing Running Processes

- Use `ps` to view process information.
  - `-f` (full) flag for detailed process information.

   ```bash
   $ ps -f
   ```

   Fields: UID, PID, PPID, CPU utilization, start time, terminal type, CPU time, and the command.

#### Stopping Processes

- For foreground processes, use CTRL + C.
- For background processes, use `kill` with the PID.

   ```bash
   $ kill 6738
   ```

   Forceful termination:

   ```bash
   $ kill -9 6738
   ```

#### Parent and Child Processes

- Each process has a PID and a Parent Process ID (PPID).
- Most user processes have the shell as their parent.

#### Zombie and Orphan Processes

- Zombie processes are dead but remain in the process table.
- Orphan processes have init as their new parent when the original parent is killed.

#### Daemon Processes

- Background processes with no controlling terminal.
- Often run with root permissions.
- Examples include printer daemons.

#### The `top` Command

- Interactive tool showing processes sorted by criteria.
- Displays information about memory, CPU usage, load averages, and active processes.

   ```bash
   $ top
   ```

#### Job ID Versus Process ID

- Job IDs are used for background and suspended processes.
- They are more convenient for handling multiple processes in a job.

Understanding process management is essential for efficiently running and controlling programs on Unix/Linux systems.