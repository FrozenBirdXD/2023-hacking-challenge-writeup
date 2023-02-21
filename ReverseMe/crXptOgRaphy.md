# One of the harder challenges: crXptOgRaphy | 50 Points
For this problem two things are provided: 
1. An encrypted message: "11 1c 14 1b 11 05 0a 0a 24 1c 2d 37 15 36 38 30 20 10 2d 1d 16 0d 35". 
2. An executable called binary-static that was used to encryt the message.
## Solution
To get flag, the message needs to be decrypted. This can be done by reverse engineering the provided file, and finding out how the message was encrypted
and reversing the process. First, to find out what kind of executable was provided, I opened the file with [IDA Freeware](https://hex-rays.com/ida-free/), 
a binary code analyser for reverse engineering. IDA automatically recognized the file as an *ELF64 for x86-64 (Executable) [elf64.dll]*, a type of Unix executable.

That's why to execute the program a Unix based system is needed. I started a virtual machine with kali linux running on it. Then I did following:
1. Opened a console

2. Changed directories to the one containing the binary-static file
3. Executed the program in the console with "./*programName*"
4. As an output the correct usage of the program was given. After the progamName a string is needed.
5. 
