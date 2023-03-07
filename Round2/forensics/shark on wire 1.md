# Description

![0](https://user-images.githubusercontent.com/125740625/223325226-22cd0ad9-9a91-44f2-8c72-75382f3e23a6.png)

# Solution 

The challenge name is a obvious reference to WireShark.

We download the given packet capture and open it using wireshark.

![1](https://user-images.githubusercontent.com/125740625/223329055-c1631ece-1cf8-468d-bd67-8eb2d533b8bc.png)

I look through the statistics and find that most of the conversations are in UDP (User Datagram Protocol).

So, I filtered udp streams and tried to find pico in it.

![4](https://user-images.githubusercontent.com/125740625/223330012-4e0518f3-3a96-4a6f-b0b9-8d29be4223cc.png)

This doesn't look useful, other than that the flag must be in UDP streams.

So I manually started looking through UDP streams.

![5](https://user-images.githubusercontent.com/125740625/223330270-ca81d771-9367-469f-82cf-2b87ccc382e9.png)

UDP stream 6 had the flag.

#### Required flag : picoCTF{StaT31355_636f6e6e}
