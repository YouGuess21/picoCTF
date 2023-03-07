# Description

![0](https://user-images.githubusercontent.com/125740625/223193454-43fbf3de-ae82-437f-a51c-ab1688fe817c.png)

# Solution

So we download the image. The challenge hints about looking into metadata.

```Image metadata is information that is embedded into files like jpeg, tiff, and other common formats. The primary form of metadata used in photos is called EXIF (Exchangeable Image File Format). This data can contain supplemental information for the image, such as the date and time that the photo was taken, with what camera model, GPS info, author, copyright information, and more.```

To look in metadata , exiftool command can be used.

![1](https://user-images.githubusercontent.com/125740625/223323982-bef43218-0b2f-4695-acfd-cc3428f2fce8.png)

Using it on given image..

![2](https://user-images.githubusercontent.com/125740625/223324205-74759481-635d-4a2f-adbf-3fd474dc09ea.png)

We can clearly the flag there...

Later, I realised  it must be a string hidden inside the image... so I can directly find it using strings command with grep.

![3](https://user-images.githubusercontent.com/125740625/223324536-87b9e686-a6c0-454e-8bdb-9a03be95f43c.png)

#### Required flag : picoCTF{s0_m3ta_fec06741}
