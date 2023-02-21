# The first warmup challenge: "Let's START" | 10 Points
We are given a text file called "letsstart.txt" with the following content:

    QIJG KIIJGMI NXPID ZDN JIGGID,  NXQ UQM IUD CIUQHUIB TÜG IUDI PADAXBHJXCIMUQFJI QZCQMUMZMUAD. NXQ TBXK BXZMIM: JQXUDDAQ{KACCBINRKAAL}  PUM TGIZDNBUFJID KGÜßID WJUMI JXMQ TAG TZMZGI
There are multiple ways to solve this problem:
1. Read the description of the challenge [here](https://www.hs-augsburg.de/Informatik/HSA-innos/Institut/White-Hats-for-Future-2023.html) and notice that the
example problem is the same as this problem. So just download it and look at the answer. Flag: **HSAINNOS{gobbledygook}**.
2. Solve it legitimately: The content of the file indicates that some kind of encoding or substitution cipher was used. With the help of an online cipher 
identifier like [this](https://www.dcode.fr/cipher-identifier) one, we can easily find out that mono-alphabetic substitution was used. Then, using a monoalphabetic 
substitution decoder like [this](https://www.dcode.fr/monoalphabetic-substitution) one, the flag can also be found easily. Flag: **HSAINNOS{gobbledygook}**. 
