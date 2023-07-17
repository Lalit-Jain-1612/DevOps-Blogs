---
title: "(Day-2):-🐧 Linux for DevOps🔁"
seoTitle: "(Day-2):-🐧 Linux for DevOps"
datePublished: Mon Jul 17 2023 04:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clk6dae6g0o39fgnvazo1ggx4
slug: day-2-linux-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689532084422/99a50448-be63-4be1-80e8-c50c45729d11.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689541780486/04fba3d4-476f-42fa-aa92-26f47eb35d87.png
tags: learning, devops, 90daysofdevops, linux-for-devops, trainwithshubham

---

Hi Techies,

This is my second blog in the journey of **#90daysofDevOps** challenge

In this blog I have listed down some basic but most important commands to kick start with Linux.

Lets start with what Linux, why Linux & how it is important for DevOps

### 🐧what is Linux?

* Linux is an open-source operating system.
    
* It serves as the foundation for computer systems and devices.
    
* It is known for its stability, security, and flexibility.
    
* Linux provides a user-friendly interface and supports various software applications.
    

### 🧐Why Linux ?

* Linux is free to use.
    
* very secure and no any antivirus needed
    
* It offers a wide range of software and tools for developers.
    
* Linux provides excellent performance and stability.
    
* It has a large and supportive community for assistance and collaboration.
    

> "Linux: The Ultimate Catalyst for DevOps Success"

### how it is important for DevOps?

* Compatibility & Flexibility: Lnux provides a flexible and customizable environment and compatible with a wide range of software tools and technologies commonly used in DevOps practices.
    
* Stability & Security: Linux is renowned for its stability, reliability and robust security provides a solid foundation and secure environment for DevOps workflows.
    
* Automation and scripting: Linux provides powerful command-line tools and scripting capabilities, enabling automation of repetitive tasks and streamlined workflows.
    
* Scalability: Linux excels at handling scalable workloads, allowing DevOps teams to efficiently manage and scale their infrastructure as needed.
    

### Basic Linux commands:

1. `ls`: List files and directories.
    
2. `cd`: Change directory.
    
3. `pwd`: Print present working directory
    
4. `mkdir`: Create a new directory.
    
5. `touch`: Create a new file.
    
6. `cp`: Copy files and directories.
    
7. `mv`: Move or rename files and directories.
    
8. `rm`: Remove files and directories.
    
9. `cat`: Display the contents of a file.
    
10. `head`: Display the first few lines of a file.
    
11. `tail`: Display the last few lines of a file.
    
12. `grep`: Search for a pattern in a file.
    
13. `man`: Display the manual page of a command.
    
14. `sudo`: Execute a command with superuser (root) privileges.
    

### Day-2 tasks of #90daysofDevOps challenge

1. **How to Check your present working directory.**
    

we can use 'pwd' command to check our current working directory as shown below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689539148573/1c2ad0d1-b562-4c13-ba99-d315adad0e36.png align="center")

here you can see firstly we change the directory to "Students1" -&gt; `cd` Students1

then 'pwd' command shows our current working directory "/home/ubuntu/Students1"

1. **List all the files or directories including hidden files.**
    

firstly I will show you how to create hidden file and hidden directory

`mkdir` .hiddenFile -&gt; this will create a hidden directory with name "hiddenFile"

`touch` .file.txt -&gt; this will create a hidden file.

here dott . plays an important role to hide your file or directory

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689539691868/0c5e531a-e1f2-4493-9a86-d7f777840d37.png align="center")

Did you see how '`ls -a`' command list down all the directories including hidden also.

1. **How to create a nested directory A/B/C/D/E**
    

we can use `mkdir -p A/B/C/D/E` to create nested directory

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689541274214/b85ba804-b68f-45f0-8bf7-9a41cb33467c.png align="center")

here '-p' denotes parent directory.

Stay tuned for blog Day 3, in upcoming blogs we will be learning some more linux commands.

Thank you!