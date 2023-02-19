# Description

![0](https://user-images.githubusercontent.com/125740625/219964870-3381c745-3d5f-4393-9e3a-eb61cd0e9017.png)

# Solution

After downloading the file, with wget I tried opening it with GUI.

![1](https://user-images.githubusercontent.com/125740625/219965204-86cf20a3-fafe-449c-9e81-645d4e8fc519.png)

Its a BMP file.. I tried to take a look at it.

![2](https://user-images.githubusercontent.com/125740625/219965329-b6c6426e-9f52-4dc3-8737-2959be817470.png)

In the line1 , few bit spell 'bad' . Searching on internet, I found this [forum](https://stackoverflow.com/questions/33483708/understanding-bmp-file) that said these are supposed to be offset and bitmapinfoheader.
Using the sample image in same forum I changed those 'bad' bits to such as that image.

![3](https://user-images.githubusercontent.com/125740625/219967709-bf32581c-7b9a-42f5-b843-ec92efbbb5be.png)      ![4](https://user-images.githubusercontent.com/125740625/219967737-73b2d3e0-f781-4634-9a8e-2da930f6c8af.png)
Then I opened the image with GUI..

![5](https://user-images.githubusercontent.com/125740625/219967787-29ff3799-b6ea-4ca6-92bf-65a641b82be7.png)

The colours look weird but atleast the image shows something... the image has notaflag{sorry} in it..and looked weirdly cropped. The width of image looks fine by the text so I decided to increase the height bits of it.

![7](https://user-images.githubusercontent.com/125740625/219967920-e55bf29d-8fc2-4c1e-b695-1423ba2291eb.png)

Here I changed them to 0B0B that is 1111 and reverted the hexdump and tried opening the file.

![8](https://user-images.githubusercontent.com/125740625/219968030-14d192fe-ead7-4b14-aedb-6a96bab45107.png)

The height seemed way too much but after zooming in a little I was able to get the flag.

![9](https://user-images.githubusercontent.com/125740625/219968069-f21c70e7-5082-4e44-8569-3e9f05c3071c.png)            ![10](https://user-images.githubusercontent.com/125740625/219968074-93453c7a-74e7-4d85-ae26-6e6b8f3cfd72.png)

Required flag : picoCTF{qu1t3_a_v13w_2020}

