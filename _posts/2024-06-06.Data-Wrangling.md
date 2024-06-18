---
 layout: post
 title: Data-Wrangling
---
- # **Data Wrangling**

---
 - Data wrangling in Linux refers to the process of cleaning, transforming, and organizing raw data into,
   a more usable format using various Linux command-line tools. This involves tasks like removing duplicates, filtering data, merging 
   files, and reformatting data. Common tools used for data wrangling in Linux include `awk`, `sed`, `grep`, `cut`, `sort`, and `uniq`. 
   These tools help automate the manipulation of text and data files, making it easier to prepare data for analysis.

 - Example Workflow
 - 1. **Extract Data:** Using tools like wget or curl to download data from web sources
        wget http://example.com/data.csv
 
 - 2. **Clean Data:** Using sed and awk to clean and format the data
        sed 's/old/new/g' data.csv | awk -F, '{print $1, $2, $3}'

 - 3. **Transform Data:** Using cut and paste to transform the data
        cut -d, -f1,3 data.csv > transformed_data.csv

 - 4. **Load Data:** Using scp or rsync to load the data to a different server or system.
        scp transformed_data.csv user@server:/path/to/destination


- # 06-06-2024

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
       
     - # **Uses of Aliases**

      - Aliases in Linux are shortcuts that allow you to create custom commands or abbreviations for longer,
        command sequences. They help save time and reduce errors by simplifying frequently used commands or creating more intuitive command names. Aliases can be temporary (for the current session) or permanent (by adding them to configuration files like .bashrc or .zshrc). 

      - Common Alias Commands
       - alias: Create or view aliases.
       - unalias: Remove an alias.

      - **Creating Temporary Aliases**
        - Basic Alias
          - alias ll='ls -la'

        - Complex Command Alias
          - alias gs='git status'

        - To list all current aliases
          - alias

        - Remove a Specific Alias
          - unalias ll

        - Remove All Aliases
          - unalias -a

     - **Making Aliases Permanent**
      - To make aliases persistent across terminal sessions, add them to your shell's configuration file,
        (e.g., .  bashrc for Bash or .zshrc for Zsh).

        - Edit Configuration File
          - nano ~/.bashrc  # or ~/.zshrc for Zsh

        - Add Aliases
          - alias ll='ls -la'
          - alias gs='git status'
          - alias grep='grep --color=auto'

        - Apply Changes
          - source ~/.bashrc  # or ~/.zshrc for Zsh

      - # Dotfiles
 
        - Dotfiles are plain text configuration files on Unix-based systems (like Linux and macOS) that are used,
          to customize and configure user environments and applications. These files are named with a leading dot (.), which makes them 
          hidden by default in directory listings. Common examples include .bashrc, .gitconfig, .vimrc, and .zshrc.

       - **Features of Dotfiles**

        - **Shell Configuration:** Files like .bashrc and .zshrc allow users to customize their command-line,
          shell  environments, setting aliases, environment variables, and shell options.

        - **Editor Settings:** Files like .vimrc and .emacs customize text editors, defining syntax,
          highlighting keybindings, and plugins.

        - **Application Configurations:** Dotfiles configure various applications, such as .gitconfig for Git,
          settings or .tmux.conf for Tmux.

       - **Common Dotfiles Examples**
          - .bashrc / .zshrc: Configuration files for Bash and Zsh shells.
          - .vimrc: Configuration for the Vim text editor.
          - .gitconfig: Configuration for Git version control.
          - .tmux.conf: Configuration for Tmux terminal multiplexer.
          - .bash_profile: Runs commands for login shells.
          - .aliases: File to store alias commands.

      - # **Remote Machines**
   
        - A remote machine, also known as a remote computer or remote server, refers to a computer that is,
          accessed and controlled over a network, typically the internet, from a different physical location.
          This allows users to perform tasks, run applications, and manage data on the remote machine as if they were physically present
 
       - **Command: SSH (Secure Shell)**
         
         - 1. **Connecting to a Remote Machine:**
             - ssh username@hostname_or_ip_address

         - 2. **Executing Commands on a Remote Machine:**
             - ssh john@example.com 'ls -l /home/john'

         - 3. **Copying Files to/from a Remote Machine:**
          
           - Copying from local to remote:
             - scp /home/user/file.txt john@example.com:/home/john/

           - Copying from remote to local:
             - scp john@example.com:/home/john/file.txt /home/user/

        - **Generating SSH Key Pair**
          
          - 1. **Generate SSH Key Pair**
           - Use the ssh-keygen command to generate a new SSH key pair. This command will create a public,
             key (id_rsa.pub) and a private key (id_rsa) in the ~/.ssh/ directory by default.

            - ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

          -2. **Copy the Public Key to Remote Machine**
           - After generating the key pair, you need to copy the public key (id_rsa.pub) to the remote,
             machine's ~/.ssh/authorized_keys file. This step allows you to authenticate using your private key without entering a 
             password.

           - ssh-copy-id username@hostname_or_ip_address

          - If ssh-copy-id is not available on your system, you can manually append the contents of,
            ~/.ssh/id_rsa.pub to ~/.ssh/authorized_keys on the remote machine.
 
           - cat ~/.ssh/id_rsa.pub | ssh username@hostname_or_ip_address 'mkdir -p ~/.ssh &&,
             cat >> ~/.ssh/ authorized_keys'
