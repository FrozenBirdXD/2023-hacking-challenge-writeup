# The second challenge in Crypto: Magical Hashtags | 50 Points
For this problem a markdown file called magical_hashtags.md is given with the following content:
### Magical Collection of Hashtags and Corresponding Magic Values

| HashTag   | Magic Values                                                                                     |
|-----------|:------------------------------------------------------------------------------------------------:|
| #bigfoot  | 69dbcecd1ec18e61a2c0353e95ab771b8cb70ceed945d63f5465513148ee396a8e419cc838e0aaac4d39ca8c79f82a36 |
| #dwarf    | 5c18211d37260aca9e0a734df296ff0db955cb6aa60e650cf43299d33fb3a2d58059aed8b6dfd8b4990d55b472461fb0 |
| #elf      | b168d9c890ec4d35018ce851011224b82d299b327c677836c9512a59abcf9e18990e3a9a58dc9df230ff0dc7591b7945 |
| #ghost    | 22cc5d882bf563efb826a7f4c288089749cee55610b13c55905f7fceee71dd1959134ba5e05739fcac8fc231c6efc582 |
| #goblin   | a7f5c623b47424a2fcfca533711531f02f392e53bf1d8e700f981b596fa19be1704cf4efac0619ab97f2d63b50cf34fa |
| #ork      | 1170882024c4da34776b86388ff02ce58a46733258a9c35438c6748f25659f6e69808acac81e44c3bd82f28aa14405fa |
| #santa    | e9a5f8295535d0492bc34fb541356fbf2d14c1b010c37bb6478b069323763ab6a12e57ed407e7ea6397dc9655ae1fb25 |
| #unicorn  | ???                                                                                              |

### Usage of Magic Values

Just put the correct magic value between HSAINNOS{ and }

## Solution
Since this is the only thing given, every "Magic Value" somehow has to correspond to each "Hashtag"and we need to find the magic value that corresponds to the 
hashtag *#unicorn*. First I tried using a 
[cipher identifier](https://www.dcode.fr/cipher-identifier) to find how what encryption algorithm was used, but with no luck. So I searched for *magic values* and
*hashtags* but that didn't help either. 

After looking at the file again, I noticed that the word *hash*tag was used and it was in the crypto category. We only need to find the magic value of the hashtag
**#unicorn**, which means that we only need to use the encryption algorithm in one way, i.e. encrypt it. Since cryptocurrencies use *hash*ing algorithms
as a fundamental component of their underlying blockchain technology, I wanted to try enrypting the hashtags with a hashing alogrithm. 

Some popular hashing algorithms are SHA-256 or Scrypt. First with an online [SHA hash creator](http://www.unit-conversion.info/texttools/sha/), I attempted to encrypt
the hashtag *#bigfoot* with well known SHA algorithms. I used SHA1, SHA224, SHA256 and finally SHA 384, which was a match. 

When *#bigfoot* was input, 
>69dbcecd1ec18e61a2c0353e95ab771b8cb70ceed945d63f5465513148ee396a8e419cc838e0aaac4d39ca8c79f82a36 

was the output, which matches the magic value in the given table. 

To confirm that SHA384 was used, I tried to encrypt the other hashtags, which also worked. So when *#unicorn* was the input,
>bc6e68dcc859a676cb144d13491637728d74bb73aecffbf848d2c1ec36cced090de97b70ca808f650d037440ff799b31

was the output.

And that was basically it. Now this magic value just has to be put between HSAINNOS{ and }. 
Flag: **HSAINNOS{bc6e68dcc859a676cb144d13491637728d74bb73aecffbf848d2c1ec36cced090de97b70ca808f650d037440ff799b31}**
