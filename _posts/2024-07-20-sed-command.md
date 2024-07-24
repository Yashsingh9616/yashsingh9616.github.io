---
 layout: post
 title: sed-command
---

`sed` (stream editor) is a Unix utility that parses and transforms text, using a simple, compact programming language. It's particularly useful for text substitution, deletion, and text file processing.

### Basic Syntax

The basic syntax of `sed` is:

```sh
sed 'command' file
```

- **command**: The `sed` command to be applied to the input text.
- **file**: The file to be processed.

### Basic Commands

1. **Substitute (`s`)**

   ```sh
   sed 's/pattern/replacement/' file
   ```

2. **Delete (`d`)**

   ```sh
   sed 'pattern d' file
   ```

3. **Print (`p`)**

   ```sh
   sed -n 'pattern p' file
   ```

4. **Append (`a`)**

   ```sh
   sed '/pattern/ a\
   new text' file
   ```

5. **Insert (`i`)**

   ```sh
   sed '/pattern/ i\
   new text' file
   ```

6. **Change (`c`)**

   ```sh
   sed '/pattern/ c\
   new text' file
   ```

7. **Transform (`y`)**

   ```sh
   sed 'y/source/destination/' file
   ```

### Examples in Detail

1. **Substitute (`s`)**

   Create a file `file.txt` with the following content:
   
   ```
   Hello World
   Hello sed
   ```
   
   Command:
   
   ```sh
   sed 's/Hello/Hi/' file.txt
   ```
   
   Output:
   
   ```
   Hi World
   Hi sed
   ```

   To replace globally in each line, use the `g` flag:
   
   ```sh
   sed 's/Hello/Hi/g' file.txt
   ```

2. **Delete (`d`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   line 3
   ```
   
   Command to delete the second line:
   
   ```sh
   sed '2d' file.txt
   ```
   
   Output:
   
   ```
   line 1
   line 3
   ```

   To delete lines matching a pattern:
   
   ```sh
   sed '/pattern/d' file.txt
   ```

3. **Print (`p`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   line 3
   ```
   
   Command to print only lines that match a pattern:
   
   ```sh
   sed -n '/line 2/p' file.txt
   ```
   
   Output:
   
   ```
   line 2
   ```

4. **Append (`a`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   ```
   
   Command to append text after lines matching a pattern:
   
   ```sh
   sed '/line 1/ a\
   new line' file.txt
   ```
   
   Output:
   
   ```
   line 1
   new line
   line 2
   ```

5. **Insert (`i`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   ```
   
   Command to insert text before lines matching a pattern:
   
   ```sh
   sed '/line 2/ i\
   new line' file.txt
   ```
   
   Output:
   
   ```
   line 1
   new line
   line 2
   ```

6. **Change (`c`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   ```
   
   Command to change lines matching a pattern:
   
   ```sh
   sed '/line 2/ c\
   new line' file.txt
   ```
   
   Output:
   
   ```
   line 1
   new line
   ```

7. **Transform (`y`)**

   Create a file `file.txt` with the following content:
   
   ```
   abc
   def
   ```
   
   Command to transform characters:
   
   ```sh
   sed 'y/abc/xyz/' file.txt
   ```
   
   Output:
   
   ```
   xyz
   def
   ```

### Advanced Examples

1. **Replace text in a specific range**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   line 3
   line 4
   ```
   
   Command to replace text in lines 2 to 3:
   
   ```sh
   sed '2,3 s/line/LINE/' file.txt
   ```
   
   Output:
   
   ```
   line 1
   LINE 2
   LINE 3
   line 4
   ```

2. **Multiple Commands**

   Create a file `file.txt` with the following content:
   
   ```
   apple
   banana
   cherry
   ```
   
   Command to apply multiple `sed` commands:
   
   ```sh
   sed -e 's/apple/APPLE/' -e 's/banana/BANANA/' file.txt
   ```
   
   Output:
   
   ```
   APPLE
   BANANA
   cherry
   ```

3. **Read from a File (`r`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   ```
   
   Create a file `insert.txt` with the following content:
   
   ```
   inserted line
   ```
   
   Command to read and insert content from another file:
   
   ```sh
   sed '/line 1/ r insert.txt' file.txt
   ```
   
   Output:
   
   ```
   line 1
   inserted line
   ```

4. **Write to a File (`w`)**

   Create a file `file.txt` with the following content:
   
   ```
   line 1
   line 2
   ```
   
   Command to write lines matching a pattern to another file:
   
   ```sh
   sed -n '/line 2/ w output.txt' file.txt
   ```
   
   This will create `output.txt` with the content:
   
   ```
   line 2
   ```

