# Description

![0](https://user-images.githubusercontent.com/125740625/219947488-c1c56ed0-a697-4684-bd60-832295e3a3ef.png)

# Solution

The file is a pcapng. I ran it in wireshark and extracted the files by using export objects with TFTP in file menu and then saved them using save all.

![2](https://user-images.githubusercontent.com/125740625/219947641-5f9eeb62-d371-4c7d-b537-e0382c4f374a.png)

We find some files in directory.. I tried opening the text files which seemed rot13 ..

![1](https://user-images.githubusercontent.com/125740625/219947770-e42bf9a5-fc72-4473-a880-c864f760099f.png)

```
TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER . FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN
I USED THE PROGRAM AND HID IT WITH - DUEDILIGENCE . CHECK OUT THE PHOTOS

```
I opened the program using GUI..

![3](https://user-images.githubusercontent.com/125740625/219948045-6cc4768f-09b9-4ac1-8bd7-aa93c29a49ab.png)

Using steghide, to extract
```
steghide extract -sf <filename>
```
It asked me for a passphrase. I used DUEDILIGENCE as instructed in plan.

![4](https://user-images.githubusercontent.com/125740625/219948305-b0f23da3-70bc-473a-bee3-fbdda6ba0f98.png)

Only picture3.bmp could be extracted ...flag.txt was created, which had the flag.

Required flag : picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

