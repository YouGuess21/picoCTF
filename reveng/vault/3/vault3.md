# Description

![vault30](https://user-images.githubusercontent.com/125740625/219928547-712d9616-b0e7-4aca-a5ef-cadfadc85004.png)

# Solution

We again get a source code with a checkPassword() that looks like this

![vault31](https://user-images.githubusercontent.com/125740625/219929672-346fcc28-5980-44c4-9d2e-869ef02e3c3f.png)

Here, password is scrambled with some for loops and at end checked with "jU5t_a_sna_3lpm18gb41_u_4_mfr340" string.
So I just wrote a reverse script

```
char a[33]={"jU5t_a_sna_3lpm18gb41_u_4_mfr340"}, b[33];
	int i;
	for(i=0; i<8; i++) 
            b[i] = a[i];
        
        for(; i<16; i++) 
            b[i] = a[23-i];
        
        for(; i<32; i+=2) 
            b[i] = a[46-i];
        
        for(i=31; i>=17; i-=2) 
            b[i] = a[i];
        
	for(i=0; i<33; i++)
		printf("%c", b[i]);
```

Required flag : picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}

