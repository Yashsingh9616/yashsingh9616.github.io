---
 layout: post
 title: awk-command
---

`awk` is a powerful programming language designed for text processing and typically used as a data extraction and reporting tool. It's a standard feature of most Unix-like operating systems.

### Basic Syntax

The basic syntax of `awk` is:

```sh
awk 'pattern { action }' file
```

- **pattern**: Specifies when `awk` performs the action.
- **action**: Specifies what `awk` does when the pattern is true.
- **file**: The file to be processed.

### Basic Examples

1. **Print all lines in a file**

```sh
awk '{ print }' file.txt
```

2. **Print the first field of each line**

```sh
awk '{ print $1 }' file.txt
```

3. **Print lines that match a pattern**

```sh
awk '/pattern/ { print }' file.txt
```

### Common `awk` Commands

1. **Print specific fields**

   Print the first and third fields of each line:
   
   ```sh
   awk '{ print $1, $3 }' file.txt
   ```

2. **Using Field Separators**

   Use a comma as a field separator:
   
   ```sh
   awk -F, '{ print $1, $2 }' file.txt
   ```

3. **Pattern Matching**

   Print lines where the first field is greater than 10:
   
   ```sh
   awk '$1 > 10 { print }' file.txt
   ```

4. **BEGIN and END Blocks**

   Execute actions before processing any lines (BEGIN) and after all lines are processed (END):
   
   ```sh
   awk 'BEGIN { print "Start" } { print } END { print "End" }' file.txt
   ```

5. **String Operations**

   Print lines where the second field contains "abc":
   
   ```sh
   awk '$2 ~ /abc/ { print }' file.txt
   ```

6. **Arithmetic Operations**

   Print the sum of the first and second fields:
   
   ```sh
   awk '{ sum = $1 + $2; print sum }' file.txt
   ```

7. **Conditional Statements**

   Print "High" if the first field is greater than 100, else print "Low":
   
   ```sh
   awk '{ if ($1 > 100) print "High"; else print "Low" }' file.txt
   ```

8. **Formatting Output**

   Print fields with formatted output:
   
   ```sh
   awk '{ printf "Name: %s, Age: %d\n", $1, $2 }' file.txt
   ```

### Examples in Detail

1. **Print all lines in a file**

   Create a file `file.txt` with the following content:
   
   ```
   Hello World
   Welcome to awk
   ```
   
   Command:
   
   ```sh
   awk '{ print }' file.txt
   ```
   
   Output:
   
   ```
   Hello World
   Welcome to awk
   ```

2. **Print the first field of each line**

   Create a file `file.txt` with the following content:
   
   ```
   John Doe 30
   Jane Smith 25
   ```
   
   Command:
   
   ```sh
   awk '{ print $1 }' file.txt
   ```
   
   Output:
   
   ```
   John
   Jane
   ```

3. **Print lines that match a pattern**

   Create a file `file.txt` with the following content:
   
   ```
   apple
   banana
   apple pie
   orange
   ```
   
   Command:
   
   ```sh
   awk '/apple/ { print }' file.txt
   ```
   
   Output:
   
   ```
   apple
   apple pie
   ```

4. **Using Field Separators**

   Create a file `file.txt` with the following content:
   
   ```
   John,Doe,30
   Jane,Smith,25
   ```
   
   Command:
   
   ```sh
   awk -F, '{ print $1, $2 }' file.txt
   ```
   
   Output:
   
   ```
   John Doe
   Jane Smith
   ```

5. **BEGIN and END Blocks**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   line 3
   ```
   
   Command:
   
   ```sh
   awk 'BEGIN { print "Start" } { print } END { print "End" }' file.txt
   ```
   
   Output:
   
   ```
   Start
   line 1
   line 2
   line 3
   End
   ```

6. **String Operations**

   Create a file `file.txt` with the following content:
   
   ```
   1 abc
   2 def
   3 abcde
   4 xyz
   ```
   
   Command:
   
   ```sh
   awk '$2 ~ /abc/ { print }' file.txt
   ```
   
   Output:
   
   ```
   1 abc
   3 abcde
   ```

7. **Arithmetic Operations**

   Create a file `file.txt` with the following content:
   
   ```
   10 20
   30 40
   ```
   
   Command:
   
   ```sh
   awk '{ sum = $1 + $2; print sum }' file.txt
   ```
   
   Output:
   
   ```
   30
   70
   ```

8. **Conditional Statements**

   Create a file `file.txt` with the following content:
   
   ```
   50
   150
   ```
   
   Command:
   
   ```sh
   awk '{ if ($1 > 100) print "High"; else print "Low" }' file.txt
   ```
   
   Output:
   
   ```
   Low
   High
   ```

9. **Formatting Output**

   Create a file `file.txt` with the following content:
   
   ```
   John 30
   Jane 25
   ```
   
   Command:
   
   ```sh
   awk '{ printf "Name: %s, Age: %d\n", $1, $2 }' file.txt
   ```
   
   Output:
   
   ```
   Name: John, Age: 30
   Name: Jane, Age: 25
   