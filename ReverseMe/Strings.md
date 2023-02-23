# So many strings!: Strings | 50 Points
For this problem, a windows executable called *Strings.exe* is provided. If you run the program nothing happens. 
### Solution
Since the file and the task are called "strings", we can assume that the task requires us to extract all the strings contained in the executable file. This can be done using a variety of tools, but for this example "**[Strings](https://learn.microsoft.com/en-us/sysinternals/downloads/strings)**" is used, one of the utilities provided by the Windows 
[Sysinternal Suite](https://learn.microsoft.com/en-us/sysinternals/) from Microsoft. 

To run the command, just type "strings" and the file to analyse behind that:
> ![example](https://user-images.githubusercontent.com/118717731/220315128-a7b252b5-c2aa-4287-83ae-48d20613adfe.png)

The output for this will be lots of Strings that are found in the specified file. In our case those are random names and methods. But only one thing is different from
the rest, and that is of interest to us:
> ![solution](https://user-images.githubusercontent.com/118717731/220316185-d220a48f-f2c2-4ce5-9ee7-c25eadccb55f.png)

If you look at the first letter or character in each row, you get the hidden flag. 

Flag: **HSAINNOS{Strings}**.
