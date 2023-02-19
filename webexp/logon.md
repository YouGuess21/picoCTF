# Description

![image](https://user-images.githubusercontent.com/125752406/219879735-5a5500a1-da81-4bfb-902f-678b4ae82b52.png)

# Solution

After opening the website, a login page opened asking for username and password.

![a](https://user-images.githubusercontent.com/125752406/219879479-e928d266-62dd-4b33-adfc-05ecae742ff4.png)

After trying to login with random username and password, the website said I was logged in but I can’t see the flag.

![image](https://user-images.githubusercontent.com/125752406/219879846-356d3b02-906f-4a9a-9ab3-1fd955251e04.png)

While trying to login as Joe it didn’t log in. 

![b1](https://user-images.githubusercontent.com/125752406/219879919-4a998d27-0d6f-44b1-a81e-f474ef5ee9c5.png)

This made me think that there’s a cookie that is storing a variable and needs to be changed.
I opened Inspect and went into Storage, there was a cookie with admin and its value was False.

![0](https://user-images.githubusercontent.com/125740625/219940299-f338e60f-3053-4d76-b9da-ca6d739c12ec.png)

Changing it to True and reloading gave me the flag.

![image](https://user-images.githubusercontent.com/125752406/219879964-1834684f-6c71-4a53-b7e5-c872f0e0cee1.png)

