# Description

![0](https://user-images.githubusercontent.com/125740625/219933695-74744550-b7ff-4506-a4d3-6b6e45041e32.png)

# Solution

We again get a source code with a checkPassword() that looks like this

![1](https://user-images.githubusercontent.com/125740625/219933703-8d25d97b-b66f-4011-b837-83bd54688130.png)

After carefullly examining the code here, first the 32 character password is taken , then first four characters are first converted to binary and then concatenated to form a 32 bit integer. Similarly, all 32 characters get converted into an array of 8 32bit integers.
To reverse this,
we convert 1096770097,1952395366,1600270708,1601398833,1716808014,1734291511,960049251,1681089078 to their binary form and divide them into 4 parts
We get:
01000001 01011111 01100010 00110001
01110100 01011111 00110000 01100110
01011111 01100010 00110001 01110100
01011111 01110011 01101000 00110001
01100110 01010100 01101001 01001110
01100111 01011111 00110000 00110111
00111001 00111001 00110000 01100011
01100100 00110011 01100010 00110110

I used following code to convert these into binary and then printed them
```
#include<stdio.h>
#include<math.h>
int convert(long long n) {
  int dec = 0, i = 0, rem;

  while (n!=0) {
    rem = n % 10;
    n /= 10;
    dec += rem * pow(2, i);
    ++i;
  }

  return dec;
}
int main()
{
        int i;
        long long a[35] = {1000001, 1011111, 1100010, 110001, 1110100, 1011111, 110000, 1100110, 1011111, 1100010, 110001, 1110100, 1011111, 1110011, 1101000, 110001, 1100110, 1010100, 1101001, 1001110, 1100111, 1011111, 110000, 110111, 111001, 111001, 110000, 1100011, 1100100, 110011, 1100010, 110110};
        char b[35];
        for(i=0; i<32; i++)
        {
            b[i]= convert(a[i]);
                printf("%c", b[i]);

        }
}

```

Required flag : picoCTF{A_b1t_0f_b1t_sh1fTiNg_07990cd3b6}
