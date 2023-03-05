 # Description
 
 ![0](https://user-images.githubusercontent.com/125740625/222962960-1ed215c3-18d7-4dc7-b407-261e69adaa5e.png)
 
 # Solution
 
 We first download the file using wget. It's an image.
 The hint was about files hidden inside hidden files (which is concept of matryoshka dolls). So, I tried using binwalk, and indeed multiple files were present inside it.
 
![2](https://user-images.githubusercontent.com/125740625/222963430-200af54f-f34a-4eb0-9698-483be4018a0a.png)

Here the zip file just contains the folder base_images again.
We enter base_images directory that contains another image, which we again binwalk. Doing this same process multiple times leads us to finally get flag.txt which contains the flag.

![3](https://user-images.githubusercontent.com/125740625/222963616-f94144d1-80d0-4616-bf00-954470f11627.png)

Required flag : picoCTF{336cf6d51c9d9774fd37196c1d7320ff}
