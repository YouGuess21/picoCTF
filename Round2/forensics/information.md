# Description

![Screenshot 2023-03-05 at 18-25-20 picoCTF - picoGym Challenges](https://user-images.githubusercontent.com/125740625/222961688-9668507f-96c0-4bfc-aaa4-7a71ddec3a1c.png)

# Solution

We download the given cat.jpg file using wget.
I tried searching for flag with strings and grep commands directly but no luck. I tried to binwalk the file, nope. I looked into its hex and saw somelines which looked like base64.

![1](https://user-images.githubusercontent.com/125740625/222962655-f74edf2e-13a1-4a97-8f7e-34a357ee2b8f.png)

We get the flag. 
Required flag : picoCTF{the_m3tadata_1s_modified}
