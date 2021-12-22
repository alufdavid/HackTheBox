after i spawn the machine i will scan for the active services:

![image](https://user-images.githubusercontent.com/89795917/147120296-408946be-d6d7-42bd-95c5-d0f524fb1865.png)

we can ping the machine to be sure its up,
after we know its up, we can use the -Pn flag 
to skip host discovery witch is being blocked:

![image](https://user-images.githubusercontent.com/89795917/147120734-6e421d4a-f22d-4a92-b8e4-bab1953d3446.png)


and look at the result of our scan:

![image](https://user-images.githubusercontent.com/89795917/147120896-fb710053-7e54-4844-b32d-6c1a80352194.png)

we see an smb port open on 445 - anonymous login:

![image](https://user-images.githubusercontent.com/89795917/147121294-40db38a6-4365-4b3e-afb9-8441d6a5aa0c.png)


and were in.

the only directory that is available with no pass is the backups:

![image](https://user-images.githubusercontent.com/89795917/147121607-34cae3cb-d8ba-4013-96d2-ce06b2e19773.png)

after we list the files in the directory we see a file name: prod.dtsConfig

we are going to get the file to our host:

![image](https://user-images.githubusercontent.com/89795917/147122003-b5366aaf-dbf0-46a9-a525-e45433f0586a.png)

as we cat into the file.
we find valuable info.

our file is a DTSconfig File:

![image](https://user-images.githubusercontent.com/89795917/147122558-389e3fe0-0747-496b-a54b-8288ca980999.png)

so we know it has to do with the SQLserver
quick look inside:

![image](https://user-images.githubusercontent.com/89795917/147122694-8dcc9eb2-202f-43ff-9cf5-c115105c7117.png)


we find username in a domainname & password.

beacuse we know from our scan that we are dealing with a microsoft SQLserver:

![image](https://user-images.githubusercontent.com/89795917/147123040-8b741347-0af6-4b46-9cb8-f2a882e97dcc.png)

we will be using the tool mssqlclient from impacket with hise windows-auth flag:

![image](https://user-images.githubusercontent.com/89795917/147123186-d0d3a3ba-cc10-433f-91bf-5bf927dffc33.png)


and with the help of the credianteils we gained earlyer were in :) :

![image](https://user-images.githubusercontent.com/89795917/147124053-f277f986-9fe8-4644-af39-b6bf934473e1.png)


