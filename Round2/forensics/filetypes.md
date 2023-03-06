# Description

![0](https://user-images.githubusercontent.com/125740625/223045527-b871379a-6a4d-4eb8-884c-2203771d6171.png)

# Solution

We download the file named 'Flag.pdf' but using file command we see that it's actually a shell archive text.

```In the Unix operating system, shar is an archive format created with the Unix shar utility. A shar file is a type of self-extracting archive, because it is a valid shell script, and executing it will recreate the files.```

After looking into it, I tried changing the extension to shar and tried executing it, but got error *uudecode not found* 

![1](https://user-images.githubusercontent.com/125740625/223048435-489e49a4-5359-4db3-8827-dea0f35f33fb.png)

So, I installed it and then tried executing it.

![2](https://user-images.githubusercontent.com/125740625/223048971-6b25d1f4-8ca5-4924-85f8-4b6c8ca4e0b0.png)

![3](https://user-images.githubusercontent.com/125740625/223049176-1e7187d4-83ca-4f75-8994-215cb2713d32.png)

We see file obtained is *current ar archive*.

```The archiver, also known simply as ar, is a Unix utility that maintains groups of files as a single archive file. The file signature is a single field containing the magic ASCII string "!<arch>"```

I tried extracting it using 

```
ar -x <filename>
```

![4](https://user-images.githubusercontent.com/125740625/223050336-7a9e819e-ff72-4211-abf0-fbb06aeb57d1.png)

Now, we have *cpio achive*.

```cpio is a general file archiver utility and its associated file format. Stands for: Copy (archive files) in and out (of an archive)```
I tried renaming then, extracting it using
```
cpio -i < <archive name>
```

![4](https://user-images.githubusercontent.com/125740625/223054142-fcd8f528-955e-462f-b3dc-b797d8d0a499.png)

We got bzip2 file, which I extracted after changing extension to .bz2.

We got gzip file, which I extracted after changing extension to .gz

We got lzip file, which I extracted after changing extension to .lz

![5](https://user-images.githubusercontent.com/125740625/223055727-0a951752-03f4-4b0a-b617-942ce8e11b71.png)

We got LZ4 file, which I extracted after changing extension to .lz4

![6](https://user-images.githubusercontent.com/125740625/223064931-efe12ba1-00ed-453d-bd98-43737aab4c1e.png)


We get LZMA file, which I extracted after changing extension to .lzma

![7](https://user-images.githubusercontent.com/125740625/223066003-bcc22233-e4aa-4433-bde9-0dd3a2615236.png)

We get lzop file, which I extracted after changing extension to .lzo

We got lzip file, which I extracted after changing extension to .lz

![8](https://user-images.githubusercontent.com/125740625/223067580-0420ac2c-6284-4a94-bea0-9db5aca44b02.png)

We got xz file, which I extracted after changing extension to .xz and using unxz

We finally get ASCII text. 
```
7069636f4354467b66316c656e406d335f6d406e3170756c407431306e5f
6630725f3062326375723137795f37396230316332367d0a
```

This looks hexadecimal, so we just convert it using any online tool.

![9](https://user-images.githubusercontent.com/125740625/223068820-6e486d0b-e73e-450b-b3d9-ab41c17621d8.png)

We get the required flag..
```
picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_79b01c26}
```





