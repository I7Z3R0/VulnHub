# Rickdiculously Easy
# Awesome machine for beginners


Lets have fun with this machine.  
  
Found that the machine is on the subnet 10.10.10.100 with the arp-scan.  
  
Initiated the nmap and found hand full of ports open, I have attached the nmap scan results as well

## Initial_Nmap:
```
# Nmap 7.80 scan initiated Fri Mar 5 10:55:56 2021 as: nmap -sC -sV -oA nmap/initial -vv -Pn 10.10.10.100  
Nmap scan report for 10.10.10.100  
Host is up, received arp-response (0.00026s latency).  
Scanned at 2021-03-05 10:55:57 PST for 36s  
Not shown: 996 closed ports  
Reason: 996 resets  
PORT STATE SERVICE REASON VERSION  
21/tcp open ftp syn-ack ttl 64 vsftpd 3.0.3  
| ftp-anon: Anonymous FTP login allowed (FTP code 230)  
| -rw-r--r-- 1 0 0 42 Aug 22 2017 FLAG.txt  
|\_drwxr-xr-x 2 0 0 6 Feb 12 2017 pub  
| ftp-syst:  
| STAT:  
| FTP server status:  
| Connected to ::ffff:10.10.10.102  
| Logged in as ftp  
| TYPE: ASCII  
| No session bandwidth limit  
| Session timeout in seconds is 300  
| Control connection is plain text  
| Data connections will be plain text  
| At session startup, client count was 2  
| vsFTPd 3.0.3 - secure, fast, stable  
|\_End of status  
22/tcp open ssh? syn-ack ttl 64  
| fingerprint-strings:  
| NULL:  
|\_ Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 4.4.0-31-generic x86\_64)  
|\_ssh-hostkey: ERROR: Script execution failed (use -d to debug)  
80/tcp open http syn-ack ttl 64 Apache httpd 2.4.27 ((Fedora))  
| http-methods:  
| Supported Methods: GET POST OPTIONS HEAD TRACE  
|\_ Potentially risky methods: TRACE  
|\_http-server-header: Apache/2.4.27 (Fedora)  
|\_http-title: Morty's Website  
9090/tcp open http syn-ack ttl 64 Cockpit web service  
| http-methods:  
|\_ Supported Methods: GET HEAD  
|\_http-title: Did not follow redirect to [https://10.10.10.100:9090/](https://10.10.10.100:9090/)  
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [https://nmap.org/cgi-bin/submit.cgi?new-service](https://nmap.org/cgi-bin/submit.cgi?new-service) :  
SF-Port22-TCP:V=7.80%I=7%D=3/5%Time=60427EBD%P=x86\_64-pc-linux-gnu%r(NULL,  
SF:42,"Welcome\\x20to\\x20Ubuntu\\x2014\\.04\\.5\\x20LTS\\x20\\(GNU/Linux\\x204\\.4\\  
SF:.0-31-generic\\x20x86\_64\\)\\n");  
MAC Address: 00:0C:29:29:93:21 (VMware)  
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux\_kernel  
  
Read data files from: /usr/bin/../share/nmap  
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
\# Nmap done at Fri Mar 5 10:56:33 2021 -- 1 IP address (1 host up) scanned in 37.16 seconds
```

## Full Nmap:

```
Nmap 7.80 scan initiated Fri Mar 5 10:57:48 2021 as: nmap -sC -sV -p- -Pn -vv -oA nmap/full 10.10.10.100  
Nmap scan report for 10.10.10.100  
Host is up, received arp-response (0.00079s latency).  
Scanned at 2021-03-05 10:57:48 PST for 45s  
Not shown: 65528 closed ports  
Reason: 65528 resets  
PORT STATE SERVICE REASON VERSION  
21/tcp open ftp syn-ack ttl 64 vsftpd 3.0.3  
| ftp-anon: Anonymous FTP login allowed (FTP code 230)  
| -rw-r--r-- 1 0 0 42 Aug 22 2017 FLAG.txt  
|\_drwxr-xr-x 2 0 0 6 Feb 12 2017 pub  
| ftp-syst:  
| STAT:  
| FTP server status:  
| Connected to ::ffff:10.10.10.102  
| Logged in as ftp  
| TYPE: ASCII  
| No session bandwidth limit  
| Session timeout in seconds is 300  
| Control connection is plain text  
| Data connections will be plain text  
| At session startup, client count was 3  
| vsFTPd 3.0.3 - secure, fast, stable  
|\_End of status  
22/tcp open ssh? syn-ack ttl 64  
| fingerprint-strings:  
| NULL:  
|\_ Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 4.4.0-31-generic x86\_64)  
|\_ssh-hostkey: ERROR: Script execution failed (use -d to debug)  
80/tcp open http syn-ack ttl 64 Apache httpd 2.4.27 ((Fedora))  
| http-methods:  
| Supported Methods: GET POST OPTIONS HEAD TRACE  
|\_ Potentially risky methods: TRACE  
|\_http-server-header: Apache/2.4.27 (Fedora)  
|\_http-title: Morty's Website  
9090/tcp open http syn-ack ttl 64 Cockpit web service  
| http-methods:  
|\_ Supported Methods: GET HEAD  
|\_http-title: Did not follow redirect to [https://10.10.10.100:9090/](https://10.10.10.100:9090/)  
13337/tcp open unknown syn-ack ttl 64  
| fingerprint-strings:  
| NULL:  
|\_ FLAG:{TheyFoundMyBackDoorMorty}-10Points  
22222/tcp open ssh syn-ack ttl 64 OpenSSH 7.5 (protocol 2.0)  
| ssh-hostkey:  
| 2048 b4:11:56:7f:c0:36:96:7c:d0:99:dd:53:95:22:97:4f (RSA)  
| ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDNvEvp4kqXX1H6FNqkKASBizY59uyLsqrLzLfT4R5vD8yuq+K0OqomxTiDwipMZTfQIRuBl2OzXX3rzRQ0aB+4EXyLbsxqNNP/+xRgPgFL6FPNI7j2rPGt+hQ6nmkpBJzzSpA4BBlGwvQt/i4LhrRoDsuD2JxQlmH1LNAlG6rE+xyqMTEgnfnO70pYzcmxDOixHiqTkbrsGnE6kIiyiOopwsR2E2KLPusFQJhEhsOOCJzurO7YYbDxQIwOMOox96SPtgti+4bnAVndLpo/IddtzZu3PB4SK43aIeGWgP7ONl6H0Cs1opW1EQSmdpww+Nu3fMlAlC+VMfmJNca8z9Np  
| 256 20:67:ed:d9:39:88:f9:ed:0d:af:8c:8e:8a:45:6e:0e (ECDSA)  
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKqM0Vcrgqds3NsV5wJ7j876UEKSpMytY6gNpa0Ey47sSAizc+hUU8UGoFmPsco2rjIn9QhdEIWzeMJksnpbxDk=  
| 256 a6:84:fa:0f:df:e0:dc:e2:9a:2d:e7:13:3c:e7:50:a9 (ED25519)  
|\_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIHJ5AJGj4+y9xHabmQ5cLyxySqPvQ9sW+ko0w1vnzZWI  
60000/tcp open unknown syn-ack ttl 64  
|\_drda-info: ERROR  
| fingerprint-strings:  
| NULL, ibm-db2:  
|\_ Welcome to Ricks half baked reverse shell...  
3 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at [https://nmap.org/cgi-bin/submit.cgi?new-service](https://nmap.org/cgi-bin/submit.cgi?new-service) :  
\==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============  
SF-Port22-TCP:V=7.80%I=7%D=3/5%Time=60427F2F%P=x86\_64-pc-linux-gnu%r(NULL,  
SF:42,"Welcome\\x20to\\x20Ubuntu\\x2014\\.04\\.5\\x20LTS\\x20\\(GNU/Linux\\x204\\.4\\  
SF:.0-31-generic\\x20x86\_64\\)\\n");  
\==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============  
SF-Port13337-TCP:V=7.80%I=7%D=3/5%Time=60427F2F%P=x86\_64-pc-linux-gnu%r(NU  
SF:LL,29,"FLAG:{TheyFoundMyBackDoorMorty}-10Points\\n");  
\==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============  
SF-Port60000-TCP:V=7.80%I=7%D=3/5%Time=60427F35%P=x86\_64-pc-linux-gnu%r(NU  
SF:LL,2F,"Welcome\\x20to\\x20Ricks\\x20half\\x20baked\\x20reverse\\x20shell\\.\\.\\  
SF:.\\n#\\x20")%r(ibm-db2,2F,"Welcome\\x20to\\x20Ricks\\x20half\\x20baked\\x20rev  
SF:erse\\x20shell\\.\\.\\.\\n#\\x20");  
MAC Address: 00:0C:29:29:93:21 (VMware)  
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux\_kernel  
  
Read data files from: /usr/bin/../share/nmap  
Service detection performed. Please report any incorrect results at [https://nmap.org/submit/](https://nmap.org/submit/) .  
\# Nmap done at Fri Mar 5 10:58:33 2021 -- 1 IP address (1 host up) scanned in 45.73 seconds


```


![[2021-04-04 02_23_17-VulnHub_machines.ctb - C__Users_Administrator_Desktop - CherryTree 0.38.11.png]]

-------------------------------------  
  
**PORT-21**  
  
Lets start the enumeration with port 21 and see whats inside.  
  
After logging with anonymous i found a txt file called FLAG.txt.

![[Pasted image 20210404022750.png]]

Lets get that file and see whats inside, After this we found one flag inside for 10 points- **FLAG{Whoa this is unexpected} - 10 Points**

![[Pasted image 20210404022832.png]]

    -------------------------------------------------  
  
**PORT-9090**  
  
We will go for port 80 at last since that has major scope.  
  
Lets move on to port 9090, As per the namp full scan it shows as http services running. Lets explore whats there.  
  
Seems like fedora page which directly gives us flag. I tried multiple ways to login but i wasnt able to i moved on from this port. - **FLAG {There is no Zeus, in your face!} - 10 Points**

![[Pasted image 20210404022910.png]]

    --------------------------------------------  
  
**PORT-13337**  
  
Lets concentrate on 13337 ports and lets try to nc to it and see what happens.  
  
Whoa!. We directly found the flag when we nc to that port - **FLAG:{****TheyFoundMyBackDoorMorty****}-10Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\1.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\1.png)  
  
\------------------------------------

    **PORT - 22222**  
  
By checking the port 22222 seems like its running the ssh service. Since we dont have any login creds we will concentrate on that later.  
  
  
\-----------------------------------------------  
  
**PORT- 60000**  
  
Lets move on to port 60000. I did nc and got a shell but however i am unable to come out of that shell due to which i have to kill the window.  
  
But however there is a another flag there lets see what it is.  
  
We got one more here lets take this as well. **FLAG{Flip the pickle Morty!} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\1.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\1.png)  
  
  
\----------------------------------------------------------------  
  
**PORT- 80**  
  
Now lets concentrate on port 80 and see whats there inside.  
  
There is nothing inside to be honest even nothing in source code as well.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\2.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\2.png)  
  
Lets search for robots.txt and see if we get something.  
  
Whoa! something is here which is useful.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\3.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\3.png)  
  
We will go inside the root\_shell.cgi and check whats inside that.  
  
I found nothing on this page but however we have tracertool and see whats there.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\4.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\4.png)  
  
Seems like it will do tracert when we put ip address, Lets put loopback address and see what happens, Sure enough it uses tracert command.  
  
We will try to investigate if we have command injection with ;  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\5.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\5.png) ![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\6.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\6.png)  
  
Lets try to get reverse shell with nc and check if that works.  
  
Indeed we got reverse shell  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\7.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\7.png)  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\8.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\8.png)  
  
  
I went one folder back and found html folder, Wanted to explore whats inside and ultimately found passwords folder and found one more called FLAG.txt.  
  
In this machine i was not able to use cat command due to which i was using the less command to open the file - **FLAG{Yeah d- just don't do it.} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\9.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\9.png) ![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\10.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\10.png)  
  
While checking password.html i found a password but however we are not sure whose password is this lets keep in back pocket(This can also be found from gobuster). **Password = winter**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\11.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\11.png)  
  
Since we have password lets see if i can cat /etc/passwd file to find the users.  
  
Wow!.. I am able to do it. So we have 3 users RickSanchez, Morty and summer. Lets try to login and see what happens  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\12.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\12.png)  
  
I tried RickSanchez and Morty but unfortunately i wasnt able to login. Lets try the last option Summer  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\13.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\13.png)  
  
Whoa!. I am able to login to Summer, I should have thought Summer == winter  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\14.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\14.png)  
  
Lets see what there.  
  
Directly found a flag in that folder and less that to find the same. **FLAG{Get off the high road Summer!} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\15.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\15.png)  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\16.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\16.png)  
  
I went one step back and found that i was able to go to the Morty folder as well which has couple of files. Lets grab those files and see what happens.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\17.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\17.png)  
  
I grabbed the files using the wget method from my local computer since python was installed on that target machine. Did python -m SimpleHTTP  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\18.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\18.png)  
  
Lets go inside the Rick and see whats there.  
  
I found RICK\_SAFE folder and got the entire folder to my computer.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\19.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\19.png)  
  
I tried to unzip the file but however it was asking for password which i dont know.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\20.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\20.png)  
  
There is an image initially i thought of Stegh and all but i usually run strings on these kind of things and luckily found the password for that zip file  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\21.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\21.png) ![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\22.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\22.png)  
  
  
So the password for that zip file is Meeseek. Lets try to unzip and see whats inside.  
  
I got one more flag of 20 points with hint about the safe. **FLAG: {131333} - 20 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\23.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\23.png)  
  
  
  
I found one binary file called safe from RICK\_SAFE folder  
  
  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\24.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\24.png)  
  
I changed the mode and tried to run the binary and seems like it requires an argument.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\25.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\25.png)  
  
I tried to run strings, ltrace and Hopper disassember but i didnt understand to be honest. Then i got thought there is something written on that previous folder about safe. Lets check it out.  
  
Then i thougt to run the binary with 131333 arugument since that previous flag has that one.  
  
OMG it worked and got the another 20 point flag as well. **FLAG{And** **Awwwaaaaayyyy** **we Go!} - 20 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\26.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\26.png)  
  
Along with that there is a hint for rick password as well. it should have 1 Uppercase character 1 digit and one of the words in my old band name.  
  
By googling i found that one of the names in old bands names are The Flesh Curtains  
  
  
Lets try to use Crunch and try to create this combination. We have got the password list which we can use with hydra for port 22222  
  
  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\27.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\27.png)  
  
  
We got to know that its for Rick only lets see if there is any hit on that with hydra.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\28.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\28.png)  
  
  
Seems like P7 curtains is the password. Lets login and try  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\29.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\29.png)  
  
Hurray!. I am able to login with the password. In the previous hint  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\30.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\30.png)  
  
  
Once i logged in i ran sudo -l to check the sudo permission and found that Rick can ALL-ALL.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\31.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\31.png)  
  
Running sudo -i and i became the root of that machine.  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\32.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\32.png)  
  
I Got the flag inside that - **FLAG: {Ionic Defibrillator} - 30 points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\33.png](file://c:\users\admini~1\appdata\local\temp\tmpmod0dl\33.png)


```
FLAG{Whoa this is unexpected} - 10 Points  
FLAG {There is no Zeus, in your face!} - 10 Points  
FLAG:{TheyFoundMyBackDoorMorty}-10Points  
FLAG{Flip the pickle Morty!} - 10 Points  
FLAG{Yeah d- just don't do it.} - 10 Points  
FLAG{Get off the high road Summer!} - 10 Points  
FLAG: {131333} - 20 Points  
FLAG{And Awwwaaaaayyyy we Go!} - 20 Points  
FLAG: {Ionic Defibrillator} - 30 points
```