---
 layout: post
 title: Data-Wrangling
---
  
 - Data wrangling in Linux refers to the process of cleaning, transforming, and organizing raw data into,
   a more usable format using various Linux command-line tools. This involves tasks like removing duplicates, filtering data, merging 
   files, and reformatting data. Common tools used for data wrangling in Linux include `awk`, `sed`, `grep`, `cut`, `sort`, and `uniq`. 
   These tools help automate the manipulation of text and data files, making it easier to prepare data for analysis.

 - Example Workflow
 - 1. **Extract Data:** Using tools like (wget or curl) to download data from web sources
        wget http://example.com/data.csv
 
 - 2. **Clean Data:** Using (sed and awk) to clean and format the data
        sed 's/old/new/g' data.csv | awk -F, '{print $1, $2, $3}'

 - 3. **Transform Data:** Using (cut and paste) to transform the data
        cut -d, -f1,3 data.csv > transformed_data.csv

 - 4. **Load Data:** Using (scp or rsync) to load the data to a different server or system.
        scp transformed_data.csv user@server:/path/to/destination


 - # **Command-Line Environment**
   ---
    - The command line environment in Linux is a text-based interface where you can type commands to interact,
      with the operating system. Instead of using a mouse to click on icons and menus, you type instructions to perform tasks like 
      managing files, running programs, and configuring the system.

     - **Job Control**
      - Job control allows you to manage multiple tasks (jobs) from a single command line session. This,
        includes   starting, stopping, resuming, and running tasks in the background or foreground. Job control is useful for 
        multitasking and managing processes efficiently without opening multiple terminal sessions.

     - **Common Job Control Commands**
       - &: Run a command in the background.
       - jobs: List all jobs in the current session.
       - fg: Bring a background job to the foreground.
       - bg: Resume a stopped job in the background.
       - Ctrl + Z: Suspend the current foreground job.
       - kill: Terminate a job or process

     - **Killing Processes**
      - Killing processes is an essential part of process management, allowing you to terminate unresponsive,
        or unnecessary processes.

     - **Common Commands for Killing Processes**
       - kill: Send a signal to a process to terminate it.
       - killall: Terminate all processes with a specific name.
       - pkill: Send a signal to processes based on name and other attributes.
       - xkill: Click on a window to kill the corresponding process (in GUI)

     - **Some Important Signals**
       - SIGTERM (15): Graceful termination, allowing the process to clean up.
       - SIGKILL (9): Forceful termination, immediately stopping the process.
       - SIGHUP (1): Hang up, often used to reload configuration.
       - SIGINT (2): Interrupt from keyboard (like Ctrl+C).
       - SIGSTOP (19): Pause the process.
       - SIGCONT (18): Continue a paused process.

     - **Practical Example**
       - Run a job in the background:
         - sleep 500 &

       - List jobs to get the job number:
         - jobs

       - Suspend the job:
         - Ctrl + Z

       - Resume the job in the background:
         - bg %1

       - Kill the job by finding its PID:
         - ps aux | grep sleep
           kill 1234  # Replace 1234 with the actual PID

     - **Terminal Multiplexer**
      - A terminal multiplexer is a tool that allows you to manage multiple terminal sessions from a single,
        screen. It is particularly useful for remote sessions, long-running processes, and complex workflows,
        that require multiple terminal windows.

      - **Common Commands in tmux**
      - **Starting tmux**
          - tmux: Start a new tmux session.
          - tmux new -s session_name: Start a new session with a specified name.
      
       - **Session Management**
          - tmux ls: List all tmux sessions.
          - tmux attach -t session_name: Attach to a named session.
          - tmux detach or Ctrl + b, d: Detach from the current session.
          - tmux kill-session -t session_name: Kill a named session.
          - tmux kill-server: Kill all tmux sessions.

       - **Window Management**
          - Ctrl + b, c: Create a new window.
          - Ctrl + b, n: Move to the next window.
          - Ctrl + b, p: Move to the previous window.
          - Ctrl + b, w: List all windows.
          - Ctrl + b, &: Kill the current window.

       - **Pane Management**
          - Ctrl + b, %: Split the current pane vertically.
          - Ctrl + b, ": Split the current pane horizontally.
          - Ctrl + b, x: Close the current pane.
          - Ctrl + b, o: Switch to the next pane.
          - Ctrl + b, ;: Toggle between the last active panes.

       - **Resizing Panes**
          - Ctrl + b, :resize-pane -L: Resize pane to the left.
          - Ctrl + b, :resize-pane -R: Resize pane to the right.
          - Ctrl + b, :resize-pane -U: Resize pane up.
          - Ctrl + b, :resize-pane -D: Resize pane down.

       - **Copy and Paste Mode**
          - Ctrl + b, [: Enter copy mode.
          - Ctrl + b, ]: Paste the copied text.

       - **GNU Screen**
          - If you prefer GNU Screen, here are some equivalent commands:

         - GNU Screen is another terminal multiplexer that provides similar functionality to Tmux. It lets you,
           run multiple terminal sessions within one window, detach them, and reattach them later, even from different locations.

       - **Starting Screen**

          - screen: Start a new screen session.
          - screen -S session_name: Start a new session with a specified name.
     
       - **Session Management**
          - screen -ls: List all screen sessions.
          - screen -r session_name: Reattach to a named session.
          - Ctrl + a, d: Detach from the current session.
          - screen -X -S session_name quit: Kill a named session.

       - **Window Management**
          - Ctrl + a, c: Create a new window.
          - Ctrl + a, n: Move to the next window.
          - Ctrl + a, p: Move to the previous window.
          - Ctrl + a, ": List all windows.
          - Ctrl + a, k: Kill the current window.
