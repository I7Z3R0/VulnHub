----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
                                                                                                        Rickdiculously Easy

                                                                                            Awesome machine for beginners




----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Lets have fun with this machine.

Found that the machine is on the subnet 10.10.10.100 with the arp-scan.

Initiated the nmap and found hand full of ports open, I have attached the nmap scan results as well

![nmap](https://user-images.githubusercontent.com/75982271/110175736-436de800-7e28-11eb-8705-5cd3f530e2f0.png)


-------------------------------------

PORT-21

Lets start the enumeration with port 21 and see whats inside.

After logging with anonymous i found a txt file called FLAG.txt.

![ftp1](https://user-images.githubusercontent.com/75982271/110175955-9182eb80-7e28-11eb-80c9-01117c736fe4.png)


Lets get that file and see whats inside, After this we found one flag inside for 10 points- FLAG{Whoa this is unexpected} - 10 Points

![ftp2](https://user-images.githubusercontent.com/75982271/110176025-ad868d00-7e28-11eb-8c3f-c6eb17256bac.png)




-------------------------------------------------

PORT-9090

We will go for port 80 at last since that has major scope.

Lets move on to port 9090, As per the namp full scan it shows as http services running. Lets explore whats there.

Seems like fedora page which directly gives us flag. I tried multiple ways to login but i wasnt able to i moved on from this port. - FLAG {There is no Zeus, in your face!} - 10 Points

![9090](https://user-images.githubusercontent.com/75982271/110176066-c727d480-7e28-11eb-9bee-3ae0b4e5af48.png)


--------------------------------------------

PORT-13337

Lets concentrate on 13337 ports and lets try to nc to it and see what happens.

Whoa!. We directly found the flag when we nc to that port - FLAG:{TheyFoundMyBackDoorMorty}-10Points



------------------------------------

PORT - 22222

By checking the port 22222 seems like its running the ssh service. Since we dont have any login creds we will concentrate on that later.


-----------------------------------------------

PORT- 60000

Lets move on to port 60000. I did nc and got a shell but however i am unable to come out of that shell due to which i have to kill the window.

But however there is a another flag there lets see what it is. 

We got one more here lets take this as well. FLAG{Flip the pickle Morty!} - 10 Points 




----------------------------------------------------------------

PORT- 80

Now lets concentrate on port 80 and see whats there inside.

There is nothing inside to be honest even nothing in source code as well.



Lets search for robots.txt and see if we get something.

Whoa! something is here which is useful.



We will go inside the root_shell.cgi and check whats inside that.

I found nothing on this page but however we have tracertool and see whats there.



Seems like it will do tracert when we put ip address, Lets put loopback address and see what happens, Sure enough it uses tracert command.

We will try to investigate if we have command injection with ;

               

Lets try to get reverse shell with nc and check if that works.

Indeed we got reverse shell






I went one folder back and found html folder, Wanted to explore whats inside and ultimately found passwords folder and found one more called FLAG.txt.

In this machine i was not able to use cat command due to which i was using the less command to open the file - FLAG{Yeah d- just don't do it.} - 10 Points

 

While checking password.html i found a password but however we are not sure whose password is this lets keep in back pocket(This can also be found from gobuster). Password = winter



Since we have password lets see if i can cat /etc/passwd file to find the users.

Wow!.. I am able to do it. So we have 3 users RickSanchez, Morty and summer. Lets try to login and see what happens



I tried RickSanchez and Morty but unfortunately i wasnt able to login. Lets try the last option Summer



Whoa!. I am able to login to Summer, I should have thought Summer == winter



Lets see what there.

Directly found a flag in that folder and less that to find the same.  FLAG{Get off the high road Summer!} - 10 Points





I went one step back and found that i was able to go to the Morty folder as well which has couple of files. Lets grab those files and see what happens.



I grabbed the files using the wget method from my local computer since python was installed on that target machine. Did python -m SimpleHTTP



Lets go inside the Rick and see whats there.

I found RICK_SAFE folder and got the entire folder to my computer.



I tried to unzip the file but however it was asking for password which i dont know.



There is an image initially i thought of Stegh and all but i usually run strings on these kind of things and luckily found the password for that zip file 

               


So the password for that zip file is Meeseek. Lets try to unzip and see whats inside.

I got one more flag of 20 points with hint about the safe. FLAG: {131333} - 20 Points





I found one binary file called safe from RICK_SAFE folder





I changed the mode and tried to run the binary and seems like it requires an argument.



I tried to run strings, ltrace and Hopper disassember but i didnt understand to be honest. Then i got thought there is something written on that previous folder about safe. Lets check it out.

Then i thougt to run the binary with 131333 arugument since that previous flag has that one.

OMG it worked and got the another 20 point flag as well. FLAG{And Awwwaaaaayyyy we Go!} - 20 Points



Along with that there is a hint for rick password as well. it should have 1 Uppercase character 1 digit and one of the words in my old band name.

By googling i found that one of the names in old bands names are The Flesh Curtains


Lets try to use Crunch and try to create this combination. We have got the password list which we can use with hydra for port 22222






We got to know that its for Rick only lets see if there is any hit on that with hydra.




Seems like P7 curtains is the password. Lets login and try



Hurray!. I am able to login with the password. In the previous hint 




Once i logged in i ran sudo -l to check the sudo permission and found that Rick can ALL-ALL.



Running sudo -i and i became the root of that machine.



I Got the flag inside that - FLAG: {Ionic Defibrillator} - 30 points









