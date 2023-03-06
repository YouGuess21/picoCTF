# Description

![0](https://user-images.githubusercontent.com/125740625/223104627-ca0cee11-13f7-49c5-81ba-63a726b3bffa.png)

# Solution

After downloading the given pcap file.. I tried opening it with wireshark as stated.

![1](https://user-images.githubusercontent.com/125740625/223110145-71f85d7a-8cec-48b3-93b9-b7d6feffa56e.png)

We see a TCP stream convo between 10.0.2.15 and 10.0.2.4 ... I tried following the stream.

![2](https://user-images.githubusercontent.com/125740625/223110736-e131ca28-b40a-45a8-86e0-fdc349624c22.png)

I saw the flag.. but with spaces which can be easily removed with tr command.

![3](https://user-images.githubusercontent.com/125740625/223110909-c5e41fce-7b54-45df-8a68-e9d44f53ffeb.png)

#### Required flag : picoCTF{p4ck37_5h4rk_b9d53765}
