# Description

![0](https://user-images.githubusercontent.com/125740625/222974964-b839453f-2640-4160-8e3d-d2184ef5830a.png)

# Solution

So this challenge, has Harry Potter references droppped all over it ( advanced-potion-making, Ron, spells ).

The file, downloaded using wget, is corrupted by spell, which are namely, jinxes and hexes. HEX....
I made its hexdump, and compared the starting few bits to know the file type..(which couldn't be determined earlier by file command {data})

![1](https://user-images.githubusercontent.com/125740625/222975322-f681cc47-057b-4f78-973c-a4e88db1139a.png)

Now comparing the starting bits to the file signatures from this ![WIKI](https://en.wikipedia.org/wiki/List_of_file_signatures) page, we get to know this is a PNG image.

But some of the bits are incorrect.

![7](https://user-images.githubusercontent.com/125740625/223011803-53e3a0e5-d75b-48b7-b458-2b9dd30d275f.png)


So I tried fixing them in nano, namely these
```89 50 4E 47 0D 0A 1A 0A 00 00 00 0D```


After reverting the hexdump, png image now opens, but its all red.

I open it using stegsolve.
I toogle through different options till, I reached  Red Plane 0.

![4](https://user-images.githubusercontent.com/125740625/223012033-f7987275-da29-4f74-b5be-2ff805682b6b.png)

##### Required flag : picoCTF{w1z4rdry}
