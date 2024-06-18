---
layout: post
title: "Devops Engineer Training"
date: 2024-06-03
---

**This is my training content!**

- # **Month Of June**

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
