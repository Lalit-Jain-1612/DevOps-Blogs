---
title: "Day 4 : Basic Linux Shell Scripting for DevOps"
seoTitle: "(Day-4) : Basic Linux Shell Scripting for DevOps"
datePublished: Thu Jul 20 2023 11:10:51 GMT+0000 (Coordinated Universal Time)
cuid: clkb1x94g00030amj6ha4eocl
slug: day-4-basic-linux-shell-scripting-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689831197319/15e544d1-fc92-4d3f-b03a-26c5da46e34f.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689851302984/48f56085-9b61-4c31-bb66-28a23d3fb0d3.jpeg
tags: linux, aws, devops, shell-scripting, 90daysofdevops

---

### What is Kernel?🧠

The kernel is like the brain of a computer's operating system. It's the central part that manages all the essential tasks, making sure everything runs smoothly. Just as our brain manages our body's functions, the kernel handles things like running programs, managing memory, and communicating with hardware devices like printers and disks. **It acts like a bridge between software and hardware**.

Without the kernel, our computer wouldn't be able to function properly, and we wouldn't be able to do all the things we love, like browsing the web, watching videos, or playing games.

### What is Shell?🐚

The **shell is a user interface** that allows users to interact with the operating system. It provides a command-line interface or a graphical interface through which users can enter commands and receive responses. **The shell understands the human-readable commands and translates them into a language that the kernel can understand**.

### What is Linux Shell Scripting?📜

It's a series of commands and instructions written in a special scripting language that can be executed by Shell.

with this scripting language we can perform various tasks like Automation, perform repetitive actions and even create our custom programs.

### Advantages of Shell Scripting in DevOps🌟:

* **Automation**: Shell scripts automate repetitive tasks, reducing manual intervention and saving time for more critical tasks.
    
* **Consistency**: Automated scripts ensure that the deployment process is consistent across different environments.
    
* **Version Control**: Shell scripts can be stored in version control systems like Git, providing a history of changes and allowing for easy collaboration.
    
* **Orchestration**: Shell scripts can be combined with other DevOps tools to create sophisticated deployment pipelines.
    
* **Flexibility**: Shell scripts can handle a wide range of tasks, from setting up environments to running tests and monitoring.
    

### What is `#!/bin/bash?` can we write `#!/bin/sh` as well?

`#!/bin/bash` which is also called a "Shebang" or "hashbang". This is at the beginning of a shell script that tells the operating system which interpreter to use to run the script. In this case, BASH(Bourne Again SHell) is being used.

we can also use `#!/bin/sh` instead of `#!/bin/bash`. But the main difference is that `#!/bin/sh` indicates that the script should be interpreted using the system's default shell.

So, you have options! You can use `#!/bin/bash` if you need Bash-specific features, and `#!/bin/sh` for more portability across different systems, as it relies on the default shell present on the system.

to check which shell is getting used by Linux we can type `which bash`,

```plaintext
ubuntu@ip-172-31-94-170:~$ which bash
/usr/bin/bash
```

### Write a Shell Script which prints "I will complete #90DaysOofDevOps challenge"

* **let's create a '.sh' file using '**`nano`**' command**
    
    ```plaintext
    nano challenge.sh
    ```
    
    above command will open a nano editor which has a straightforward and user-friendly interface, making it easier to use. It provides on-screen shortcuts at the bottom.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689841482025/bc900906-57b5-4c3c-92d8-df3d4fef46f0.png align="center")
    
    now to save the content and exit the editor press <mark>'ctrl+X' then 'Y' and 'ENTER'.</mark>
    
* **to make '.sh' file executable we need to give permission using** `chmod`
    
    ```plaintext
    chmod 777 challenge.sh
    ```
    
    either we can use `bash <filename.sh>` or '`./'` notation before &lt;`filename.sh`\&gt; to execute '`.sh`' file. (By using "./" before the script name, you explicitly tell the shell to look for the script in the current directory).
    
    <mark>Note</mark> : Don't give space between './' and '&lt;filename.sh\`&gt;'
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689841795442/5042486b-6054-467b-8fa9-8c3aae83f1ef.png align="center")
    
    ### Write a Shell Script to take user input, input from arguments and print the variables.
    
    create a "`user-input.sh`" file using `nano` editor
    
    ```plaintext
    nano user-input.sh
    ```
    
    now let's create a script,
    
    ```plaintext
                                                                                
    #!/bin/bash
    
    echo "Enter your name: "
    
    read name
    
    age=$1
    
    echo "I am ${name}"
    echo "My age is "$age""
    ```
    
    here,
    
* `read` : command is used to take input from user.
    
* `age=$1` : means only one argument is provided and its value has assigned to variable "age". (<mark>Note: dont give space before and after '=' operator</mark>) or else you will get an error "[user-input.sh](http://user-input.sh): line 7: age: command not found".
    

`${name}` : $ symbol helps to access the value stored in a variable or perform substitution operations and the curly braces, {}, are used to delimit the variable name and separate it from surrounding characters.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689848354485/106a9d8d-806e-466b-94fd-a2f778e26db6.png align="center")

### Write an Example of If else in Shell Scripting by comparing 2 numbers

crate a file '`if-else.sh`' using `nano`,

```plaintext
#!/bin/bash

#read input from user

read -p "Enter first number: " num1
read -p "Enter second number: " num2

#write condition to comapre two numbers

if [ $num1 -gt $num2 ]; then
 echo "$num1 is greater than $num2"
elif [ $num1 -lt $num2 ]; then
 echo "$num1 is less than $num2"
else
 echo "Both numbers are equal"
fi
```

here,

* `read -p "Enter first number`: " num1 : '-p' is used to prompt the user to "Enter first number".
    
* `if [ $num1 -gt $num2 ];` It's crucial to be <mark>mindful of spaces</mark> when using the "if" statement and the "\[" (test) command in shell scripting. There is a space after the "if" keyword, a space before and after the opening square bracket "\[", and a space before and after the closing square bracket "\]".
    
* \-gt : is greater than
    
* \-lt : is less than
    
* \-eq : equal
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689850573344/87652967-07e4-452b-ad4b-989923b88447.png align="center")

Thank you for reading...😊!

Discover essential Linux commands in my previous blog! 👉[(Day-3): Basic Linux Commands](https://hashnode.com/post/clk8g51s9000h0amo4l8adyny). Learn to navigate, manage files, and boost your Linux skills. Whether you're a beginner or a seasoned user, there's valuable knowledge for everyone. Happy exploring! 🐧🚀