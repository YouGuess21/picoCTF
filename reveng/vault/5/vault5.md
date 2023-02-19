# Description

![0](https://user-images.githubusercontent.com/125740625/219931979-e86353c9-15d4-4df4-9dc1-db5918a4ac5c.png)

# Solution

We again get a source code with a checkPassword() that looks like this

![1](https://user-images.githubusercontent.com/125740625/219932023-321088ce-74a4-4019-981b-31368dd817f9.png)

Here, first password is URL encoded than base64 encoded and checked with concatenation of "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm" + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2" + "JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2"
![2](https://user-images.githubusercontent.com/125740625/219932245-9e7b91b0-ccea-4cbe-8077-0bd9e8e5425c.png)

We get "%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%30%62%39%35%37%63%34%66" which if decoded in any urldecoder gives us

Required flag : picoCTF{c0nv3rt1ng_fr0m_ba5e_64_0b957c4f}
