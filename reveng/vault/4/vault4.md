# Description

![1](https://user-images.githubusercontent.com/125740625/219931574-7f27a40b-f8cf-4ff5-877b-7a1dd5ef4e1b.png)

# Solution

We again get a source code with a checkPassword() that looks like this

![2](https://user-images.githubusercontent.com/125740625/219931630-d3f712ed-c7fa-4f65-afd0-f0fd64cac34c.png)

We see that instead of text ascii and hexadecimal values are used, so if I just print it in compiler I will get the password

```
int i;
	char a[100]={106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0143, 061 ,
            '9' , '4' , 'f' , '7' , '4' , '5' , '8' , 'e'};
	for(i=0; i<32; i++)
  	printf("%c", a[i]);
	
```
Required flag : picoCTF{jU5t_4_bUnCh_0f_bYt3s_c194f7458e}
