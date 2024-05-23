#### Capturing the flag

we are given with the website http://74.225.254.195:2324/

after carefully inspecting the source code for the gallery tab we find that the images are loaded by 
http://74.225.254.195:2324/getFile?file=/home/kaptaan/PClub-DVWA/static/images/gallery/3.jpeg

Now we have to find the routes.txt file so searching for routes.txt using this getfile method link in different levels of the directory 

![img](https://github.com/anirudh802/capture-the-flag/blob/main/Screenshot%20from%202024-05-23%2019-18-49.png)

we find http://74.225.254.195:2324/getFile?file=/home/kaptaan/PClub-DVWA/routes.txt gives the routes.txt file

in the routes.txt file we find the first flag

###### pclub{path_trav3rsa1_1s_fun}

also we fing two routes Ip details and Seceratory login
and also the hint to use command injection
now trying to use command injections in both of these paths

now we see that os injections work in the Ip details tab.
i first used ifconfig to get the macadderss
we get the next flag.

######  60:45:bd:af:3f:e5

Now trying other commands in the ipDetails tab
we find that whoami returns kaptaan.


now i tried grep after a bunch of commands and it worked

so i injected grep -r "pclub{" in the tab. And voila.
we get the third flag

###### pclub{01d_1s_g01d_sql1}

now continuing with grep i tried grep -r 'pclub' and a bunch of things popped up.

So now i tried grep -r '' to get every readable file
i got everything that was stored and readable including the README.md file
the whole output of the grep command is saved as the crack file in the repo


The readme.md file contained all the steps to get everything till the fourth flag which after further inspection was stored at 
/static/files/amansg22/ariitk.jpeg

using the username:password pairs stored in readme file,
we access amansg22 to get ariitk.jpeg
![img](https://github.com/anirudh802/capture-the-flag/blob/main/ariitk%20(1).jpeg)

and again using aperisolve to extract steghide file we get a qr which after scanning a base64 encoded string
the string is rot13 encoded 

after decoding we get

###### pclub{data_1s_3v3ryth1ng}

now the last task was pwn and crypto which after trying to get something out of i seriously could not

