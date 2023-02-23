# An encrypted flag?: HEXHEX | 10 Points
For this problem the encrypted flag is given in a String: "485341494E4E4F537B69735448495363727970746F6772617068793F7D".

## Solution
Here, the same procedure as in the other warmup challenge can be used to solve the task.
1. Using an online [chipher identifier](https://www.dcode.fr/cipher-identifier) we can see that the flag most likely just is ASCII code.
2. To test this hypothesis, an online [ASCII converter](https://www.dcode.fr/ascii-code) can be used to convert the String into text, revealing the flag.
3. In this way, we find out that the flag was just ASCII code in hexadecimal. 

Flag: **HSAINNOS{isTHIScryptography?}**.
