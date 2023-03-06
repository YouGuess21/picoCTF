# Description

![0](https://user-images.githubusercontent.com/125740625/223183670-d4cd6a51-d1ed-4bfc-ac46-2f208a0b9582.png)

# Solution

We get the given gzip file extract it, mmls the .img file.

```t
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/diskdisksleuth$ mmls dds2-alpine.flag.img 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000262143   0000260096   Linux (0x83)
```

They asked us to find file named *down-at-the-bottom.txt* . 

So, I tried extracting disk image by binwalk.
Then I forgot the find argument, so I just 
```
find * | grep <filename>
```
and we got file location.

![9](https://user-images.githubusercontent.com/125740625/223188823-26658574-6acc-4d20-a597-36a9b05d53af.png)

To get the given flag I used 
```
cat _dds2-alpine.flag.img.extracted/ext-root/root/down-at-the-bottom.txt | tr -d ' ' | tr -d '(,),_,-,/,\' | tr -d '\n'
Output: picoCTF{f0r3ns1c4t0rn0v1c30ba8d02d}
```
then manually added _ .

#### Required flag :  picoCTF{f0r3ns1c4t0r_n0v1c3_0ba8d02d}
