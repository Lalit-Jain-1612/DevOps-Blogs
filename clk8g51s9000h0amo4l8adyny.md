---
title: "(Day-3): Basic Linux Commands"
seoTitle: "(Day-3): Basic Linux Commands"
datePublished: Tue Jul 18 2023 15:25:31 GMT+0000 (Coordinated Universal Time)
cuid: clk8g51s9000h0amo4l8adyny
slug: day-3-basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689652843123/179ea1e8-f1de-453a-bea9-1a72c5dc5afc.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689693897503/518e437c-6ae8-4fd8-8f65-d7671932b933.jpeg
tags: linux, aws, devops, linux-commands, 90daysofdevops

---

Hi Techies,

In this Day 3 blog post of the #90daysofDevOps challenge, I will present an introduction to fundamental Linux commands and offer demonstrations to enhance your understanding.

---

### The following commands will be covered:

`cat` - To view content of the file

`chmod` - To change the access permissions of the file

`history` - To see history of the commands that you ran

`rm/rmdir` - To remove file/directory

`vi` - To add contents in a file

`head` - To show Top lines from the file

`tail` - To show the bottom lines from the file

`diff` - To find difference between files

---

1. ### To view what's written in a file.
    
    we can use `cat` command to view the content of file
    

```plaintext
ubuntu@ip-172-31-94-170:~$ cat fruits.txt 
Apple
Mango
Banan
Cherry
Kiwi
Orange
Guava
```

1. ### To change the access permissions of files.
    

The `chmod` command in Linux is used to change or modify the access permissions of files and directories. It stands for "change mode" and is often used to control who can read, write, or execute a file. The command can be used by the file owner or a superuser with administrative privileges

```plaintext
                     chmod <permissions> <file(s)
```

Replace `<permissions>` with a numeric code or symbolic representation representing the desired permissions, and `<file(s)>` with the name of the file you want to modify.

Numeric representation: Symbolic representation:

`4`: Read(r) `u`: User/owner

`2`: Write(w) `g`: Group

`1`: Execute(x) `o`: others

`a`: all(user, group and others)

**to grant read and write permission to user and read permission to group and no any permission to others**

```plaintext
chmod 640 <filename>
```

* The first digit, `6`, indicates read (`4`) and write (`2`) permissions for the owner, which adds up to `6`.
    
* The second digit, `4`, signifies read permission for the group.
    
* The third digit, `0`, represents no permissions for others.
    

**alternate command for same**

```plaintext
chmod u=rw,g=r,o= <filename>
```

1. ### To check which commands you have run till now.
    

"history" command is used to check the history of commands.

```plaintext
ubuntu@ip-172-31-94-170:~$ history
    1  echo "Hello lalit"
    2  date
    3  pwd
    4  cd /
    5  pwd
    6  ls
    7  cd bin
    8  ls
    9  /bin
   10  cd ..
```

1. ### To remove a directory/ Folder.
    
    `rm` and `rmdir` are used to remove file and directory respectively
    

```plaintext
rm <filename>
rmdir <directoryname>
```

here `rmdir` command will remove only empty directory

to remove non-empty directory(recursive directory) we should add `-r` after rm where 'r' stands for "recursive"

```plaintext
rm -r <directoryname>
```

below example for `rm`,`rmdir` and `rm -r` where 'A' is non-empty directory.

```plaintext
ubuntu@ip-172-31-94-170:~$ ls
A  folderB  folderC  fruits.txt  mazedaar

ubuntu@ip-172-31-94-170:~$ rm fruits.txt
ubuntu@ip-172-31-94-170:~$ ls
A  folderB  folderC  mazedaar

ubuntu@ip-172-31-94-170:~$ rmdir folderB
ubuntu@ip-172-31-94-170:~$ ls
A  folderC  mazedaar

ubuntu@ip-172-31-94-170:~$ rmdir A
rmdir: failed to remove 'A': Directory not empty

ubuntu@ip-172-31-94-170:~$ rm -r A
ubuntu@ip-172-31-94-170:~$ ls
folderC  mazedaar
```

1. ### To create a fruits.txt file and to view the content.
    

we have many ways to create a file:

1. Using touch command: The `touch` command is commonly used to create an empty file. For example, `touch filename.txt` will create a file named "filename.txt" in the current directory.
    
    ```plaintext
    ubuntu@ip-172-31-94-170:~$ ls
    folderC  mazedaar
    ubuntu@ip-172-31-94-170:~$ touch fruits.txt
    ubuntu@ip-172-31-94-170:~$ ls
    folderC  fruits.txt  mazedaar
    ubuntu@ip-172-31-94-170:~$
    ```
    
2. Using echo command: The `echo` command can be used to create a file with content. For example, `echo "Hello, World!" >> filename.txt` will create a file named "filename.txt" and write the text "Hello, World!" to it.
    
    where '&gt;' will overwrite the file with new content
    
    '&gt;&gt;' will append the content to the file without overwriting
    
    ```plaintext
    ubuntu@ip-172-31-94-170:~$ ls
    folderC  fruits.txt  mazedaar
    ubuntu@ip-172-31-94-170:~$ echo "hello world" >> Shark.txt
    ubuntu@ip-172-31-94-170:~$ ls
    Shark.txt  folderC  fruits.txt  mazedaar
    ubuntu@ip-172-31-94-170:~$ cat Shark.txt
    hello world
    ```
    
    When used with the `-e` option, `echo` recognizes and interprets the escape sequences in the provided string. Here are some commonly used escape sequences:
    
    * `\n`: Represents a newline character, causing a line break.
        
    * `\t`: Represents a horizontal tab character, creating a tab indentation.
        
    * `\"`: Represents a double quotation mark, allowing the inclusion of quotes in the echoed text.
        
    * `\\`: Represents a backslash character, enabling the inclusion of a backslash in the echoed text.
        
    
    For example, `echo "Hello\nWorld"` would display:
    
    ```plaintext
    Hello\nWorld
    ```
    
    ```plaintext
    ubuntu@ip-172-31-94-170:~$ echo "Tomato\nBrinjal\nPeas" >> vegetables.txt
    ubuntu@ip-172-31-94-170:~$ cat vegetables.txt 
    Tomato\nBrinjal\nPeas
    ```
    
    while `echo -e "Hello\nWorld"` would display:
    
    ```plaintext
    Hello
    World
    ```
    
3. Using redirection operators: You can create a file and input content using redirection operators. For example, `cat > filename.txt` allows you to enter text directly into the terminal, and pressing **Ctrl+D** will save the entered text as the content of the file.
    
    ```plaintext
    ubuntu@ip-172-31-94-170:~$ cat > language.txt
    python
    cpp
    javascript
    shell script
    ubuntu@ip-172-31-94-170:~$ cat language.txt 
    python
    cpp
    javascript
    shell script
    ubuntu@ip-172-31-94-170:~$
    ```
    
4. Using text editors: Text editors like `nano`, `vim/vi` provide a more interactive way to create and edit files. For example, `vim company.txt` will open the vim editor named **company.txt** as shown below
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689685881989/e4156178-11f4-425d-8d5e-f72f6a3ab8e7.png align="center")
    

**press 'i' to enter the INSERT mode.**

**press 'esc' and then type :wq to save and quit.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689686544877/d10ab2f8-7b66-407a-8e6c-d23d8c6b4e7b.png align="center")

1. ### To Show only top three fruits and only bottom three fruits from the file
    
    to get top three fruits we can use `head -n 3 <filename.txt>` or `head -3 <filename.txt>` and for bottom three fruits `tail -n 3 <filename.txt>` or `tail -3 <filename.txt>` where '-n' denotes the number of lines we want to dsiplay.
    
    Example,
    

```plaintext
ubuntu@ip-172-31-94-170:~$ vi fruits.txt
ubuntu@ip-172-31-94-170:~$ cat fruits.txt 
Apple
Banana
Papaya
Kiwi
Cherry
Strawberry
ubuntu@ip-172-31-94-170:~$ head -3 fruits.txt 
Apple
Banana
Papaya
ubuntu@ip-172-31-94-170:~$ tail -n 3 fruits.txt 
Kiwi
Cherry
Strawberry
ubuntu@ip-172-31-94-170:~$
```

1. ### To find the difference between fruits.txt and Colors.txt
    
    diff command is used to find the difference between two files
    
    syntax: `diff <file1> <file2>`
    
    When working with `diff`, it is crucial to know how to interpret the output, which consists of:
    
    * Output starting with `<` refers to the content in the first file.
        
    * Output starting with `>` refers to the content in the second file.
        
    * Line numbers corresponding to the first file.
        
    * A special symbol. Special symbols indicate how the first file needs to be edited to match the second file. The output may display:
        
        * `a` (add)
            
        * `c` (change)
            
        * `d` (delete)
            
    * Line numbers corresponding to the second file.
        
    
    **create two sample files using** `vi editor`
    

after adding content, files will look like,

**fruits.txt**,

```plaintext
ubuntu@ip-172-31-94-170:~$ vi fruits.txt
ubuntu@ip-172-31-94-170:~$ cat fruits.txt 
Apple
Mango
Banana
Cherry
Kiwi
Orange
Guava
```

**colors.txt,**

```plaintext
ubuntu@ip-172-31-94-170:~$ vi colors.txt
ubuntu@ip-172-31-94-170:~$ cat colors.txt 
Red
Pink
White
Black
Blue
Orange
Purple
Grey
```

**difference between fruits.txt and colors.txt**

```plaintext
ubuntu@ip-172-31-94-170:~$ diff fruits.txt colors.txt 
1,5c1,5
< Apple
< Mango
< Banana
< Cherry
< Kiwi
---
> Red
> Pink
> White
> Black
> Blue
7c7,8
< Guava
---
> Purple
> Grey
```

lets look at the output:

<mark>1,5c1,5</mark> : line 1 to 5(1,5) from fruits.txt should be **changed**(c) to line 1 to 5(1,5) from colors.txt

<mark>&lt; Apple,&lt; Mango, &lt; Banana, &lt; Cherry, &lt; Kiwi</mark> : The content you **need to change**.

<mark>&gt; Red, &gt; Pink, &gt; White, &gt; Black, &gt; Blue</mark> : The content you **need to change it to**

<mark>7c7,8</mark> : line 7 from fuits.txt should be **changed**(c) to line 7 and 8(7,8) from colors.txt

<mark>&lt;Guava</mark> : The content you need to change.

<mark>&gt; Purple, </mark> \&gt; Grey : The content you need to change it to

Thank you for reading this blog!

If you want learn about Linux architecture and the importance of Linux for DevOps then please check out my previous blog👇

[(Day-2):-Linux for DevOps](https://lalitjain.hashnode.dev/day-2-linux-for-devops)