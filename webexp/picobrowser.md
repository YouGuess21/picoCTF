# Description

![0](https://user-images.githubusercontent.com/125740625/219952356-60393340-f833-422e-a02f-f55a34cf8af9.png)

# Solution

I opened the given and saw the following

![1](https://user-images.githubusercontent.com/125740625/219952427-cb129641-e5b4-4657-aa95-8c4fd8df8363.png)

After a quick Google Search, I got to know that websites know our browser by user-agent. A simple way to change User-Agent is to curl the link in terminal and use -A to specify User-Agent
```
curl <link> -A <user-agent>
```
![1](https://user-images.githubusercontent.com/125740625/219952911-73e2567e-ec60-47f7-85fa-60b2546c73cc.png)

Here we see the flag 

```t
<div class="jumbotron">
            <p class="lead"></p>
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{p1c0_s3cr3t_ag3nt_e9b160d0}</code></p>
            <!-- <p><a class="btn btn-lg btn-success" href="admin" role="button">Click here for the flag!</a> -->
            <!-- </p> -->
        </div>
```
We see the 
Required flag : picoCTF{p1c0_s3cr3t_ag3nt_e9b160d0}
