# Description

![0](https://user-images.githubusercontent.com/125740625/223423574-fd0cadf8-228f-4a0f-9988-4f926327d35d.png)

# Solution

We download the given file, its gzip which I extracted to get disk image.

Its partitions are as ...

![1](https://user-images.githubusercontent.com/125740625/223424700-81f585b6-42e2-4245-b302-79e16b823012.png)

Just like previous sleuthkit challenges, I tried to extract its contents with binwalk command, and grep pico.

![3](https://user-images.githubusercontent.com/125740625/223428271-ffd4cc5d-47d4-42e2-8e2a-6e00cc973dca.png)

I then, tried to search for file named flag... but I couldn't do so like previously so I tried this command..

```
find . -name  '*flag*'
```

![2](https://user-images.githubusercontent.com/125740625/223429863-fcfde6e2-bb6c-4168-99d4-f034623f8eca.png)

I tried thus found data file...
and

![4](https://user-images.githubusercontent.com/125740625/223430197-943ce19d-d4e1-4e40-be78-1957362160d8.png)

#### Required flag : picoCTF{by73_5urf3r_adac6cb4}
