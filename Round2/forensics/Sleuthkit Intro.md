# Description

![0](https://user-images.githubusercontent.com/125740625/223116087-fc3c3e98-9356-4910-bec9-65e13c7f4284.png)

# Solution

I downloaded the given file ,which appears to be gzip, looking at its size exclaimed something that I normally don't while downloading picoCTF files, nor does my girlfriend, ever. (sike, I don't have gf, am lonely af, and yes just blinked twice.)

![1](https://user-images.githubusercontent.com/125740625/223117319-012ed898-9665-4f48-9cf9-43ce6e59a419.png)

```The Sleuth Kit is a library and collection of Unix- and Windows-based utilities for extracting data from disk drives and other storage so as to facilitate the forensic analysis of computer systems.```

Upon extracting gzip file we get .img file

```An IMG file is a disk image file created by various disk imaging applications, such as H+H Software Virtual CD. It stores an exact copy of the data on a CD or DVD and is used for backups and burning new discs.```

Description said to use mmls command on the file ... so here we go.

![2](https://user-images.githubusercontent.com/125740625/223122880-879925b5-1bcc-4e5e-b7e1-1cf658e381dc.png)

Linux length : 202752

We connect to remote checker service and give it the length.  

![4](https://user-images.githubusercontent.com/125740625/223123843-e489a962-2f74-4a29-9649-075fa9ade26a.png)

#### Required flag : picoCTF{mm15_f7w!}
