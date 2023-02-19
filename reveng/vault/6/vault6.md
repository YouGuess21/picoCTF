# Description

![0](https://user-images.githubusercontent.com/125740625/219932500-7110032a-a995-4d42-9769-8e9c4b00253d.png)

# Solution

We again get a source code with a checkPassword() that looks like this

![1](https://user-images.githubusercontent.com/125740625/219932564-236734ea-871f-47fd-9753-89fe6cec5e3f.png)

Here, password is XOR'ed with 0x55 which is equal to myBytes, so we just need to myBytes ^ 0x55 to get password, with following

```
int i;
        char a[100]={0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36};
        for(i=0; i<32; i++)
            printf("%c", a[i]^0x55);        
```
We get required flag : picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc}         
