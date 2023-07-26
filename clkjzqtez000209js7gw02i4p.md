---
title: "(Day-5) : Advanced Linux commands"
seoTitle: "(Day-5) : Advanced Linux Commands"
datePublished: Wed Jul 26 2023 17:19:47 GMT+0000 (Coordinated Universal Time)
cuid: clkjzqtez000209js7gw02i4p
slug: day-5-advanced-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690190761859/cad97336-ef04-44e6-be7a-b3ef96de903b.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690391947716/24fbe377-e7e4-4e4e-be77-1602cad738fa.webp
tags: linux, aws, 90daysofdevops, trainwithshubham, advanced-linux

---

### User management:

1. how to add a new user
    
    * In case you are root user and want to add new user then syntax would be `useradd options username`
        
    * In case you are non-root user then syntax would be: `sudo useradd options username`
        
        1. `sudo` command stands for 'superuser do'. It allows non-root user to run command as the superuser(root) by giving administrative privileges.
            
        2. `useradd`: will create a new user account.
            
        3. options: There are many options we can use with useradd command. for example:
            
            \-m = It is used to create a home directory of newly added user.
            
        4. username: replace username with the desired username for new user.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690298828129/49174436-b0b9-412c-8f71-9b1e6ddb8b33.png align="center")
            
            `ls /home` : to see all your user home directory
            
            as you can see `sudo useradd shahrukh` doesn't create home directory for user 'shahrukh', however `sudo useradd -m salman` does create home directory for 'salman'.
            
2. how to set password for user
    
    ```plaintext
    sudo passwd username
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690300400794/57f49f96-65e5-490c-9387-6319e2370539.png align="center")
    
3. how to check all the existing user accounts
    
    ```plaintext
    cat /etc/passwd
    ```
    
4. how to delete user account
    
    ```plaintext
    sudo userdel username
    ```
    

### Group management:

Group is a collection of users.

why do we need groups: suppose you are a devOps engineer and in your company there are many employees some of them are developers, some are testers and some are devOps engineer. So for different different users there will be different permissions and suppose if any new employee joins the company as a developer so instead of assigning permissions individually we add that new employee to a group named "developer" and we can assign permissions to that "developer" group only.

1. how to create a new group
    
    ```plaintext
    sudo groupadd groupname
    ```
    
    **Note**: whenever you create a new user (`sudo useradd -m <username>`), by default a group with the same name as user gets created.
    
2. how to check newly added group
    
    ```plaintext
    cat /etc/group
    ```
    
3. how to add a user to a group
    
    * command to add a single user to a single group
        
        ```plaintext
        sudo usermod -aG groupname username
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690366976841/92d47d28-5376-4e2f-828a-dd9317240ca8.png align="center")
        
        here `-aG` : G is used to create the new list of supplementary GROUPS and -a is used to append the user to the supplemental GROUPS mentioned by the -G option without removing the user from other groups.
        
        ```plaintext
        ubuntu@ip-172-31-94-170:~$ cat /etc/group
        root:x:0:
        daemon:x:1:
        bin:x:2:
        sys:x:3:
        adm:x:4:syslog,ubuntu
        tty:x:5:
        devops:x:1016:testers
        testers:x:1017:
        ```
        
        as you can see a group "devops" is created and the user "testers" is a member of "devops" group.
        
        If you want to see group memebership of a particular user then use command: `groups <username>`
        
        ```plaintext
        ubuntu@ip-172-31-94-170:~$ groups testers
        testers : testers devops
        ubuntu@ip-172-31-94-170:~$
        ```
        
    * command to add a user to multiple groups at a time
        
        ```plaintext
        sudo usermod -aG group1,group2,... username
        ```
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690373558562/c1279d90-3109-41b1-b9f1-92445bb509cf.png align="center")
        
    * command to add multiple users to a group
        
        ```plaintext
        sudo gpasswd -M user1,user2,... groupname
        ```
        
        Please note that the `-M` option of `gpasswd` is used specifically to modify the group members. If the group had existing members before running this command, they will be removed from the group, and only the specified users will be members after the operation.
        
        use `members <groupname>` command to see all the users belonging to a particular group.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690375178103/cfa77af4-e0c7-4165-b7a3-e4f0a4dd6495.png align="center")
        
        as you can see `gpasswd -M` command removed the user 'testers' and got overrided by user 'salman' and 'shubham'
        
4. how to delete user from a group
    
    ```plaintext
    sudo gpasswd -d username groupname
    ```
    

### grep(Global Regular Expression Print):

1. `grep` is used for searching and pattern matching in text. It searches for lines within one or more text files that match a specified pattern or regular expression and prints those lines as output.
    
    syntax :
    
    ```plaintext
    grep [options] pattern file(s) 
    ```
    
    **Options:** `grep` supports various options that modify its behavior. Some commonly used options include:
    
    * `-i`: Ignore case when searching. This makes `grep` case-insensitive.
        
    * `-v`: Invert the match. Print lines that do not match the pattern.
        
    * `-r` or `-R`: Recursively search for the pattern in directories and subdirectories.
        
    * `-n`: Print line numbers along with matching lines.
        
    * `-l`: Print only the names of files containing the pattern, not the matching lines.
        
    * `-c`: Print only the count of matching lines, not the lines themselves.
        
    * `-w`: Match whole words only, not substrings.
        
    
    lets create a file "application.log"
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690385025174/7b9c8478-3879-4d73-9379-505ef10827b4.png align="center")
    
    `grep 'TRACE' application.log` will give all the lines containing the word 'TRACE'
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690384928322/a62aa32e-e8dc-4ba5-af8e-198608453b87.png align="center")
    
    `grep -c 'TRACE' application.log`, -c will give total count of lines containing word 'TRACE'
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690385448667/94998449-2e37-4db8-98ff-25352865e091.png align="center")
    
    grep using regular expression
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690388385838/a2b1e49d-9758-4c3b-8235-b5c0e504eddd.png align="center")
    
    we need to use the `-E` option to enable extended regular expression syntax.
    
    `'^(Virat|sachin)'` this command searches for lines that starts with Virat or sachin.
    

### awk command

It is primarily used for data extraction, manipulation, and reporting. AWK reads text files line by line, splits each line into fields, and then performs operations based on predefined patterns and actions.

syntax :

```plaintext
awk '/pattern/ { action }' input_file
```

* for example, to print the first 20 lines of the `application.log` file where the word "TRACE" appears, you can use the following `awk` command:
    
    ```plaintext
    awk 'NR>=1 && NR<=20 && /TRACE/ {print NR,$1,$2,$3}' application.log
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690390543845/66a9eccf-d913-4e84-b553-f5266580f644.png align="center")
    
    * `NR`: Represents the current line number.
        
    * `NR>=1 && NR<=20`: This condition specifies that we want to process lines 1 to 20 in the file.
        
    * `/TRACE/`: This checks if the whole line contains the word "TRACE".
        
    * `print $1, $2, $3`: If the line contains "TRACE", it prints the first, second and third fields (columns) of that line.
        

### find command

It is used to search for files and directories within a specified directory hierarchy based on various criteria such as filename, size, ownership, modification time, and more.

syntax:

```plaintext
find <path> <expression> <action>
```

for example, to find all files with a specific extension (e.g., `.txt`) in the current directory and its subdirectories:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690391338251/73073ef9-6982-4444-8a17-629bef41a5bd.png align="center")

`-type f` represent the type of file you want to search for.

`-name pattern`: Searches for files and directories whose names match the specified `pattern` (.txt).

Thank you for reading 😊....!

Read my previous blog to learn about [Basic Linux Shell Scripting](https://hashnode.com/post/clkb1x94g00030amj6ha4eocl).