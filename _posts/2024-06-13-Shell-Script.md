---
 layout: post
 title: Shell-Scripting
---

   - Shell scripting is a powerful way to automate tasks in Unix-based operating systems, including Linux and macOS.
     It involves writing scripts using shell commands to perform a sequence of operations automatically. Shell scripts can 
     simplify complex tasks, automate repetitive tasks, and enhance productivity.

   - **Features of Shell Scripting**
   
    - Automation:
       - Automates repetitive tasks.
       - Schedules tasks using cron jobs.

    - Efficiency:
       - Reduces manual effort.
       - Speeds up the execution of tasks.
 
    - Flexibility:
       - Scripts can be modified to handle different tasks.
       - Supports conditional statements and loops.

    - **Uses of Shell Scripting**

       - System Administration
       - File Management
       - Networking
       - Development
       - Data Processing

   ---

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
