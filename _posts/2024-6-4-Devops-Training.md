---
layout: post
title: "Devops Engineer Training"
date: 2024-06-03
---

**This is my training content!**

- **First Week In Month Of June**

- # **(03-06-2024)**

- **What is kernel and its functions?**
    ---
     - The Linux® kernel is the main component of a Linux operating system (OS) and is the core interface between,
       a computer’s hardware and 
       its processes.
     - It communicates between the 2, managing resources as efficiently as possible.
     - The kernel is so named because—like a seed inside a hard shell—it exists within the 
     - OS and controls all the major functions of the hardware, whether it’s a phone, laptop, server, or any,
       other kind of computer.

  - **What the kernel does**
    ---
     The kernel has 4 jobs:
     1. **Memory management:** Keep track of how much memory is used to store what, and 
        where.
     2. **Process management:** Determine which processes can use the central processing 
        unit (CPU), when, and for how long.
     3. **Device drivers:** Act as mediator/interpreter between the hardware and processes.
     4. **System calls and security:** Receive requests for service from the processes.
    ---
- **How to check the kernel version?**
   ---
    - To check kernel function name: --
    - root@localhost ~]# uname -r
    - 5.14.0-284.11.1.el9_2.x86_64
   ---
   ---
- **Types of kernel**
   ---
    - 1. Monolithic kernel
          - Description: The kernel that manages the system's resources between the system application and,
            the system hardware is known as the Monolithic kernel. Here, the kernel and user services are implemented and run in the same address space.
          - Examples: Linux, Unix.
    - 2. Micro kernel
          - Description: Minimizes the amount of code running in kernel mode. Essential services such as,
            device drivers, protocol stacks, and file systems run in user space.
          - Examples: Minix, QNX
   ---

- # **What is shell in linux?**
   ---
    -  A command line is a text-based interface which can be used to input instructions to a 
       computer system. 
       The Linux command line is provided by a program called the shell. Over the long history of UNIX-like systems, many shells have been developed.


- **Common Shell Commands**
   ---
    - 1. File Operations:

         - ls: List directory contents.
         - cp: Copy files or directories.
         - mv: Move or rename files or directories.
         - rm: Remove files or directories.
         - touch: Create an empty file.

    - 2. Text Processing:

         - cat: Concatenate and display file content.
         - grep: Search text using patterns.
         - awk: Pattern scanning and processing language.
         - sed: Stream editor for filtering and transforming text.
         - wc: Word, line, character, and byte count.
          
    - 3. System Monitoring:

         - top: Display tasks and system status.
         - ps: Report a snapshot of current processes.
         - df: Report file system disk space usage.
         - du: Estimate file space usage.
   
   - 4. Networking:

         - ping: Check the network connection to a server.
         - ifconfig: Configure a network interface.
         - scp: Securely copy files between hosts.
         - ssh: Secure Shell for remote login.

   - 5. Scripting Specific:

         - echo: Display a line of text.
         - read: Read a line of input.
         - #!/bin/bash: Shebang to specify the script's interpreter.
         - chmod +x script.sh: Make a script executable.
         - ./script.sh: Execute the script.



- **What is FOSS?**
   ---
    - FOSS means Free and Open Source Software. It doesn’t mean the software is free of cost. 
      It means that the software's source code is open for all and anyone is free to use, study and modify the code.
      This principle allows others to contribute to developing and improving a software like a community.
- **What is Open Source Software?**
   ---
    - Open Source Software is something that you can modify as per your needs, and share with others without,
      any licensing violation burden. When we say Open Source, the source code of the software is available,
      publicly with Open Source licenses like GNU (GPL) which allows you to edit the source code and distribute it.

- **What is Jekyll?**
   ---
    - 1. Jekyll theme is a static website generator that is designed for building minimal, static blogs and pages
         to be hosted on GitHub Pages. With the help of Jekyll, it strips everything down to the bare minimum, eliminating a lot of complexity. We can easily transform our plain text into static website pages and blogs.
      2. The main advantage of Jekyll is it requires no database and CMS systems or any updates like in the case,
         of WordPress. It supports static HTML, CSS, JavaScript, and even Markdown, so with the help of markdown, you can create awesome blog posts. What’s best is it goes well with GitHub-Pages and It loads faster.

- **What is WordPress?**
  ---
   - 1. Simply, WordPress is a web publishing software that is used to create beautiful websites or blog websites.
     2. On a more high level, WordPress is a content management system written in PHP that uses a MySQL database. 
        In Layman’s language, WordPress is the simplest and most powerful blogging and website builder as WordPress powers over 43% of all the websites on the Internet in existence today plus WordPress is an open-source content management system licensed under GPLv2.
     3. The best part of WordPress is you can create any type of website with WordPress from blog websites,
        to e-commerce to business and portfolio websites or anything.

- # 04-06-2024 #

- # **Shell Script**
   ---
    - Shell scripting is a powerful way to automate tasks in Unix-based operating systems, including Linux,
      and macOS. It involves writing scripts using shell commands to perform a sequence of operations automatically. Shell scripts can simplify complex tasks, automate repetitive tasks, and enhance productivity.

   - Features of Shell Scripting
    - 
   - Automation:
      - Automates repetitive tasks.
      - Schedules tasks using cron jobs.

   - Efficiency:
      - Reduces manual effort.
      - Speeds up the execution of tasks.
 
   - Flexibility:
      - Scripts can be modified to handle different tasks.
      - Supports conditional statements and loops.

   - Uses of Shell Scripting

     - System Administration
     - File Management
     - Networking
     - Development
     - Data Processing


   **Step 1:** Shebang and Script Initialization
    - #!/bin/bash

   **Step 2:** Variables
    - #!/bin/bash

      # Variable declaration
      NAME="John"
      AGE=30
      echo "My name is $NAME and I am $AGE years old."

   **Step 3:** Comments
    - #!/bin/bash

      # This is a single-line comment
      :'
      This is a multi-line comment.
      It can span multiple lines.
      '
      OR
      <<comments
      This is second comment.
      It is multiple lines.
      comments

   **Step 4:** Input and Output
    - #!/bin/bash

      echo "Enter your name: "
      read NAME
      echo "Hello, $NAME!"
   
   **Step 5:** Conditional Statements
    - Conditional statements allow the script to make decisions based on certain conditions.
      if-else
    - #!/bin/bash

      echo "Enter a number: "
      read NUMBER

      if [ $NUMBER -gt 10 ]; then
         echo "The number is greater than 10."
      else
         echo "The number is less than or equal to 10."
      fi

    case
    - #!/bin/bash

      echo "Enter a letter: "
      read LETTER

      case $LETTER in
         [a-z] )
            echo "You entered a lowercase letter." ;;
         [A-Z] )
            echo "You entered an uppercase letter." ;;
        * )
            echo "You entered a non-alphabetic character." ;;
      esac

   **Step 6:** Loops
    - Loops are used to execute a block of code repeatedly.
      for Loop
      - #!/bin/bash

       for i in {1..5}
       do
          echo "Iteration $i"
       done

      while Loop
      - #!/bin/bash

        COUNTER=1

        while [ $COUNTER -le 5 ]
        do
          echo "Iteration $COUNTER"
         ((COUNTER++))
        done

   **Step 7:** Functions
    - Functions are reusable blocks of code that can be called with a name.
    - #!/bin/bash

      # Function definition
      greet() {
         echo "Hello, $1!"
      }

      # Function call
      greet "Alice"
      greet "Bob"
   
   **Step 8:** File Operations
    - Shell scripts can perform various file operations like reading, writing, and copying files.
    - Reading a File
    - #!/bin/bash

      FILE="sample.txt"

      while IFS= read -r line
      do
        echo "$line"
      done < "$FILE"

    - Writing to a File
     - #!/bin/bash

       echo "This is a sample text" > output.txt
       echo "Appending text" >> output.txt

    - Copying a File
     - #!/bin/bash

       cp source.txt destination.txt

   **Step 9:** Command Line Arguments
    - Shell scripts can accept arguments from the command line.
    - #!/bin/bash

       echo "Script name: $0"
       echo "First argument: $1"
       echo "Second argument: $2"

   **Step 10:** Error Handling
    - Handle errors using exit statuses and error messages.
    - #!/bin/bash
        FILE="nonexistent.txt"
         if [ -f "$FILE" ]; then
            echo "File exists."
         else
            echo "File does not exist."
            exit 1
         fi



- **PuTTY**
   ---
    - PuTTY is a free and open-source terminal emulator, serial console, and network file transfer application. 
      It supports various network protocols, including SSH, Telnet, rlogin, and SCP. PuTTY is primarily used for securely connecting to remote servers and network devices.
   - **Features:**
      - Terminal Emulation
      - Protocol Support
      - Session Management
      - Customization
   - **Uses:**
      - Remote Server Management
      - Remote Server Management
- **PuTTYgen**
   ---
    - PuTTYgen is a key generator tool for creating SSH keys, which are used to secure SSH connections.
   - **Features:**
      - Key Generation
      - Key Conversion
   - **Uses:**
      - SSH Key Generation
      - Key Management
      - Key Conversion

- # 05-06-2024

- # **Vim (Editors)**
   
   ---
    - Vim (Vi IMproved) is a highly configurable text editor built to enable efficient text editing.
      It is, an enhanced version of the older vi editor, and it is commonly used in the Unix and,
      Linux environments. Vim is known for its powerful features and extensive customization options,
      which make it a favorite among programmers and system administrators.

    - Functions and Features of Vim 
     - 1. **Modes:** Vim operates in several modes, each serving a different purpose:
           - Normal Mode: The default mode for navigation and manipulation of text.
           - Insert Mode: Mode for inserting text.
           - Visual Mode: Mode for selecting blocks of text.
           - Command-Line Mode: Mode for executing commands.

     - 2. **Editing:**
           - i, a, o: Enter insert mode at different positions (before the cursor, after the cursor, on a new line).
           - d, c, y: Delete, change, and yank (copy) text.
           - p, P: Paste text after or before the cursor.

     - 3. **Deleting and Changing Text**
           - x: Delete character under the cursor.
           - dd: Delete the current line.
           - dw: Delete the current word.
           - d$: Delete to the end of the line.
           - cw: Change the current word.
           - c$: Change to the end of the line.

     - 4. **Copying and Pasting**
           - yy: Yank (copy) the current line. 
           - yw: Yank the current word.
           - p: Paste after the cursor.
           - P: Paste before the cursor.

     - 5. **Saving and Exiting**
           - :w: Save the file.
           - :q: Quit Vim.
           - :wq: Save and quit.
           - :q!: Quit without saving.
           - ZZ: Save and quit (shortcut for :wq).
           - :e filename: Open a new file.
           - :split, :vsplit: Split the window horizontally or vertically.


     - 6. **Navigation:**
           - h, j, k, l: Move left, down, up, right. 
           - w, b: Move to the start of the next or previous word.
           - 0, $: Move to the beginning or end of the line.
           - gg: Go to the top of the file.
           - G: Go to the bottom of the file.

     - 7. **Undo/Redo:**
           - u: Undo And Ctrl-r: Redo.

     - 8. **Search and Replace:**
          - /pattern: Search for a pattern.
          - :s/old/new/g: Substitute old text with new text.


- **Data Wrangling**

- # 06-06-2024

 - # **Command-Line Environment**

 - # **Git**


- # 07-06-2024
 - **hello**
