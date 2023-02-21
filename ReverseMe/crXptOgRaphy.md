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
>![1](https://user-images.githubusercontent.com/118717731/220437188-cba349f6-bbfb-4714-b436-7830bc232832.png)
2. Changed directories to the one containing the binary-static file
>![2](https://user-images.githubusercontent.com/118717731/220436142-6d9d107d-cf14-48fd-a844-eab66ae682d5.png)
3. Executed the program in the console with "./*programName*"
>![3](https://user-images.githubusercontent.com/118717731/220435563-1d2f9ecf-56c0-4ab9-8579-cc51a7bc6bd7.png)
4. As an output the correct usage of the program was given. After the progamName a string is needed. So I added *Hello*
>![4](https://user-images.githubusercontent.com/118717731/220435848-728f36ee-f607-4d6d-a13f-78451edc06ca.png)

-> The program takes a string as an input and prints the encrypted string as a hexadecimal to the console.

To analyse how the program encrypts the string, I opened it with [ghidra](https://ghidra-sre.org/). A software reverse engineering (SRE) suite of tools developed 
by NSA's Research Directorate.

After opening the program with ghidra and letting it analyse it, we can see lots of options for us to do. I did these steps:
1. In the Symbol tree, we can search for a main function and get a result. By clicking on it, we get the disassembled code of the program in assembly language. 
>![2](https://user-images.githubusercontent.com/118717731/220441863-de55bde6-3f37-4913-ad38-c5814f289773.png)
2. This shows what the program does and therefore how it encrypts the text. But since reading assembly code is very tedious, we can decompile the main method 
into a more readable code in C:
```C
undefined8 main(int param_1,undefined8 *param_2)

{
  undefined8 uVar1;
  size_t sVar2;
  char *__src;
  long in_FS_OFFSET;
  int local_fc;
  char local_f8 [112];
  byte local_88 [104];
  long local_20;
  
  local_20 = *(long *)(in_FS_OFFSET + 0x28);
  if (param_1 == 2) {
    strcpy(local_f8,(char *)param_2[1]);
    __src = local_f8;
    strcpy((char *)local_88,__src);
    encrypt((char *)local_88,(int)__src);
    printf("Encrypted message (in hex): ");
    local_fc = 0;
    while( true ) {
      sVar2 = strlen((char *)local_88);
      if (sVar2 <= (ulong)(long)local_fc) break;
      printf("%02x ",(ulong)local_88[local_fc]);
      local_fc = local_fc + 1;
    }
    putchar(10);
    uVar1 = 0;
  }
  else {
    printf("Usage: %s <plaintext>\n",*param_2);
    uVar1 = 1;
  }
  if (local_20 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return uVar1;
}
```
3. All this code does, in simple words is: It just takes the string that was inputed by the user and calls the function *encrypt()*. Then it displays the encryped
value as a hexadecimal. So we need to investigate what the function *encrypt()* does to the string. After decompiling we get:
```C

void encrypt(char *__block,int __edflag)

{
  byte bVar1;
  size_t sVar2;
  int local_2c;
  
  local_2c = 0;
  while( true ) {
    sVar2 = strlen(__block);
    if (sVar2 <= (ulong)(long)local_2c) break;
    bVar1 = __block[local_2c];
    sVar2 = strlen("YOUR_KEY_HERE");
    __block[local_2c] = bVar1 ^ "YOUR_KEY_HERE"[(ulong)(long)local_2c % sVar2];
    local_2c = local_2c + 1;
  }
  return;
}
```
4. The function implements a simple encryption algorithm that operates on the characters in the provided string. The key used for the encryption is a fixed string "YOUR_KEY_HERE". The algorithm uses the bitwise XOR operator to combine the bytes of the original string with the bytes of the key, in a repeating pattern. The encrypted string is returned as output. 

    This can be used to decrypt a message because XOR is a reversible operation: if you XOR a value with a key, and then XOR the result again with the same key, you get back the original value. The following code in Java does this for us (This can also be done with the code in C, but I wanted to try coding it in Java :ok_hand:):

```Java
import java.util.Scanner;

public class DecryptMessage {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter the encrypted message: ");
        String encryptedMessage = sc.nextLine();

        String[] encryptedHex = encryptedMessage.split(" ");
        String key = "YOUR_KEY_HERE";
        String decryptedMessage = "";

        for (int i = 0; i < encryptedHex.length; i++) {
            int encryptedChar = Integer.parseInt(encryptedHex[i], 16);
            int keyChar = (int) key.charAt(i % key.length());
            int decryptedChar = encryptedChar ^ keyChar;
            decryptedMessage += (char) decryptedChar;
        }

        System.out.println("Decrypted message: " + decryptedMessage);
    }
}
```
5. This code asks the user for the encrypted string in a hexadecimal format and applies the XOR operation with the key from above. Then the decryped message is printed
to the console.

  When we give the program the encryped message "11 1c 14 1b 11 05 0a 0a 24 1c 2d 37 15 36 38 30 20 10 2d 1d 16 0d 35" provided by the challenge, this is the output:

> Decrypted message: HSAINNOS{ThePowerOfXOR}

This is the flag for the problem. Flag: **HSAINNOS{ThePowerOfXOR}**.
