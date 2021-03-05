    ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
Rickdiculously Easy  
  
Awesome machine for beginners  
  
  
  
  
\----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
  
Lets have fun with this machine.  
  
Found that the machine is on the subnet 10.10.10.100 with the arp-scan.  
  
Initiated the nmap and found hand full of ports open, I have attached the nmap scan results as well  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\1.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\1.png)  
  
  
\-------------------------------------  
  
**PORT-21**  
  
Lets start the enumeration with port 21 and see whats inside.  
  
After logging with anonymous i found a txt file called FLAG.txt.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\2.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\2.png)  
  
Lets get that file and see whats inside, After this we found one flag inside for 10 points- **FLAG{Whoa this is unexpected} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\3.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\3.png)  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\4.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\4.png)  
  
  
\-------------------------------------------------  
  
**PORT-9090**  
  
We will go for port 80 at last since that has major scope.  
  
Lets move on to port 9090, As per the namp full scan it shows as http services running. Lets explore whats there.  
  
Seems like fedora page which directly gives us flag. I tried multiple ways to login but i wasnt able to i moved on from this port. - **FLAG {There is no Zeus, in your face!} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\5.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\5.png)  
  
  
\--------------------------------------------  
  
**PORT-13337**  
  
Lets concentrate on 13337 ports and lets try to nc to it and see what happens.  
  
Whoa!. We directly found the flag when we nc to that port - **FLAG:{TheyFoundMyBackDoorMorty}-10Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\6.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\6.png)  
  
\------------------------------------  
  
**PORT - 22222**  
  
By checking the port 22222 seems like its running the ssh service. Since we dont have any login creds we will concentrate on that later.  
  
  
\-----------------------------------------------  
  
**PORT- 60000**  
  
Lets move on to port 60000. I did nc and got a shell but however i am unable to come out of that shell due to which i have to kill the window.  
  
But however there is a another flag there lets see what it is.  
  
We got one more here lets take this as well. **FLAG{Flip the pickle Morty!} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\7.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\7.png)  
  
  
\----------------------------------------------------------------  
  
**PORT- 80**  
  
Now lets concentrate on port 80 and see whats there inside.  
  
There is nothing inside to be honest even nothing in source code as well.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\8.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\8.png)  
  
Lets search for robots.txt and see if we get something.  
  
Whoa! something is here which is useful.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\9.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\9.png)  
  
We will go inside the root\_shell.cgi and check whats inside that.  
  
I found nothing on this page but however we have tracertool and see whats there.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\10.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\10.png)  
  
Seems like it will do tracert when we put ip address, Lets put loopback address and see what happens, Sure enough it uses tracert command.  
  
We will try to investigate if we have command injection with ;  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\11.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\11.png) ![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\12.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\12.png)  
  
Lets try to get reverse shell with nc and check if that works.  
  
Indeed we got reverse shell  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\13.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\13.png)  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\14.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\14.png)  
  
  
I went one folder back and found html folder, Wanted to explore whats inside and ultimately found passwords folder and found one more called FLAG.txt.  
  
In this machine i was not able to use cat command due to which i was using the less command to open the file - **FLAG{Yeah d- just don't do it.} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\15.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\15.png) ![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\16.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\16.png)  
  
While checking password.html i found a password but however we are not sure whose password is this lets keep in back pocket(This can also be found from gobuster). **Password = winter**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\17.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\17.png)  
  
Since we have password lets see if i can cat /etc/passwd file to find the users.  
  
Wow!.. I am able to do it. So we have 3 users RickSanchez, Morty and summer. Lets try to login and see what happens  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\18.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\18.png)  
  
I tried RickSanchez and Morty but unfortunately i wasnt able to login. Lets try the last option Summer  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\19.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\19.png)  
  
Whoa!. I am able to login to Summer, I should have thought Summer == winter  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\20.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\20.png)  
  
Lets see what there.  
  
Directly found a flag in that folder and less that to find the same. **FLAG{Get off the high road Summer!} - 10 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\21.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\21.png)  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\22.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\22.png)  
  
I went one step back and found that i was able to go to the Morty folder as well which has couple of files. Lets grab those files and see what happens.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\23.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\23.png)  
  
I grabbed the files using the wget method from my local computer since python was installed on that target machine. Did python -m SimpleHTTP  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\24.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\24.png)  
  
Lets go inside the Rick and see whats there.  
  
I found RICK\_SAFE folder and got the entire folder to my computer.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\25.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\25.png)  
  
I tried to unzip the file but however it was asking for password which i dont know.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\26.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\26.png)  
  
There is an image initially i thought of Stegh and all but i usually run strings on these kind of things and luckily found the password for that zip file  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\27.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\27.png) ![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\28.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\28.png)  
  
  
So the password for that zip file is Meeseek. Lets try to unzip and see whats inside.  
  
I got one more flag of 20 points with hint about the safe. **FLAG: {131333} - 20 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\29.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\29.png)  
  
  
  
I found one binary file called safe from RICK\_SAFE folder  
  
  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\30.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\30.png)  
  
I changed the mode and tried to run the binary and seems like it requires an argument.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\31.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\31.png)  
  
I tried to run strings, ltrace and Hopper disassember but i didnt understand to be honest. Then i got thought there is something written on that previous folder about safe. Lets check it out.  
  
Then i thougt to run the binary with 131333 arugument since that previous flag has that one.  
  
OMG it worked and got the another 20 point flag as well. **FLAG{And Awwwaaaaayyyy we Go!} - 20 Points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\32.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\32.png)  
  
Along with that there is a hint for rick password as well. it should have 1 Uppercase character 1 digit and one of the words in my old band name.  
  
By googling i found that one of the names in old bands names are The Flesh Curtains  
  
  
Lets try to use Crunch and try to create this combination. We have got the password list which we can use with hydra for port 22222  
  
  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\33.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\33.png)  
  
  
We got to know that its for Rick only lets see if there is any hit on that with hydra.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\34.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\34.png)  
  
  
Seems like P7 curtains is the password. Lets login and try  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\35.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\35.png)  
  
Hurray!. I am able to login with the password. In the previous hint  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\36.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\36.png)  
  
  
Once i logged in i ran sudo -l to check the sudo permission and found that Rick can ALL-ALL.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\37.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\37.png)  
  
Running sudo -i and i became the root of that machine.  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\38.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\38.png)  
  
I Got the flag inside that - **FLAG: {Ionic Defibrillator} - 30 points**  
  
![file://c:\users\admini~1\appdata\local\temp\tmp_brgox\39.png](file://c:\users\admini~1\appdata\local\temp\tmp_brgox\39.png)