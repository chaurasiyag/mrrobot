# mrrobot
Based on the Mr. Robot show, can you root this box?
Can you root this Mr. Robot styled machine? This is a virtual machine meant for beginners/intermediate users. There are 3 hidden keys located on the machine, can you find them?


# MRROBOT
## First I enumerated the ip 
`` nmap -sV -A ip``

The thing was found that was : invalid digital certificate . But I knew that it is used for valid source authetication and for data integrity. This was not much usefull for me.

and That was running wordpress website.
## Then enumerated the direcrtory

```dirsearch -u 10.10.24.186 -w /usr/share/wordlists/dirb/big.txt```
In between I gone through all the instruction which was available on the website one file was found but that was not much useful for me .

Found some directory :

![ alt text ]("/home/kalg/Screenshots/result.png")

### gone through everyone:
Found a base64 text in /license directory 

Then decoded and tried for wp-login.php web directory and It was succesful. 
## Shell Spawning

In Themes section  ,edited the file 404.php with php-reverse-shell file's content and turned on a listener nc -lvnp 1234.

Now to run that I went at  this location
```https://10.10.24.186/wp-content/themes/twentyfifteen/404.php```

### Found a shell owned by daemon
Then went to /home/ directory and found ```/home/robot``` directory .In this folder two files were available but not accesible ,as they are owned by `robot` user.


So decided for privilege escalation.

I got the kernal version and serached for exploit then I found a kernal vulnerability for privilege escalation and found c code , run it but not worked.

Now transfered the linPeas.sh file in /tmp and run it.

Found some command for which suid was set one of them was nmap .
 Then run
  ``` /usr/local/bin/nmap --interactive ```

 ``` !sh```


## Hurray buddy you are root now!!
