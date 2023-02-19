# Description

![0](https://user-images.githubusercontent.com/125740625/219943721-f6186d42-e778-41cc-b9d2-1b479ca1251f.png)

# Solution

Firstly, I downloaded the file using wget and tried opening it.

![1](https://user-images.githubusercontent.com/125740625/219944039-8e20b9cd-e9ab-439f-81c0-7622f41c2edc.png)

![2](https://user-images.githubusercontent.com/125740625/219944089-52e144f8-212b-420e-ad31-c2084f778150.png)

![4](https://user-images.githubusercontent.com/125740625/219944093-69f73626-97c5-46eb-b629-1e50ea287bab.png)

Dialogue box says file contains macros. To find embedded files, I used binwalk command and long list of files appeared.

![3](https://user-images.githubusercontent.com/125740625/219944215-15e38582-b3a3-49d4-ab53-bc996fc31f6f.png)

I extracted it using 
```
binwalk -e <file-name>
```
Using tree command I looked for anything which help me with flag

![5](https://user-images.githubusercontent.com/125740625/219944490-5b7dfa0e-0f4d-4ac5-8e3a-9a7f8a076ed7.png)

I cat the hidden file, which looked like base64 encoded....so I used sed to replace the spaces with nothing and base64 decoded it with base64 -d command.

![6](https://user-images.githubusercontent.com/125740625/219944752-1b582951-4a81-4425-820a-ef86388e299b.png)

Required flag : picoCTF{D1d_u_kn0w_ppts_r_z1p5}
