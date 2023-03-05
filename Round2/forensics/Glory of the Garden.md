# Description

![0](https://user-images.githubusercontent.com/125740625/222963911-bb7a2c56-1a00-4a8e-ad8a-fda7dc084328.png)

# Solution 

We wget the file, its comparatively larger file. Hint said about hex editing.
So, 

```t
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/garden$ xxd garden.jpg garden
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/garden$ ls
garden  garden.jpg
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/garden$ grep pico garden
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/garden$
```
No matches.
So I tried just looking directly for flag in .jpg file.

```
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/garden$ strings garden.jpg | grep pico
Here is a flag "picoCTF{more_than_m33ts_the_3y3657BaB2C}"
```
I got the flag.
Upon revisting, I realised word pico might be broken into two different lines in hex hence...

```
youguess@youguess-Inspiron-14-5410-2-in-1:~/Downloads/picoctf/forensics/garden$ grep CTF garden -C 5
00230520: 1046 07b5 7216 df7e 5ff7 c576 363f ebab  .F..r..~_..v6?..
00230530: b70d 18ce 3ccd 6a7e 6b8d af56 b579 39ca  ....<.j~k..V.y9.
00230540: eeef 53ae 8620 31b8 751f 9514 f7fb cff5  ..S.. 1.u.......
00230550: a2bb bdac 9687 98e4 d3b2 e87f ffd9 4865  ..............He
00230560: 7265 2069 7320 6120 666c 6167 2022 7069  re is a flag "pi
00230570: 636f 4354 467b 6d6f 7265 5f74 6861 6e5f  coCTF{more_than_
00230580: 6d33 3374 735f 7468 655f 3379 3336 3537  m33ts_the_3y3657
00230590: 4261 4232 437d 220a                      BaB2C}".
```

Required flag : picoCTF{more_than_m33ts_the_3y3657BaB2C}
