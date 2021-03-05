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

![13337](https://user-images.githubusercontent.com/75982271/110176261-06562580-7e29-11eb-98e4-239271ba6b43.png)

------------------------------------

PORT - 22222

By checking the port 22222 seems like its running the ssh service. Since we dont have any login creds we will concentrate on that later.


-----------------------------------------------

PORT- 60000

Lets move on to port 60000. I did nc and got a shell but however i am unable to come out of that shell due to which i have to kill the window.

But however there is a another flag there lets see what it is. 

We got one more here lets take this as well. FLAG{Flip the pickle Morty!} - 10 Points 

![60000](https://user-images.githubusercontent.com/75982271/110176316-1968f580-7e29-11eb-9164-5ad3a16b6e15.png)


----------------------------------------------------------------

PORT- 80

Now lets concentrate on port 80 and see whats there inside.

There is nothing inside to be honest even nothing in source code as well.

![1](https://user-images.githubusercontent.com/75982271/110176394-36052d80-7e29-11eb-9fda-f41e95a1ef06.png)

Lets search for robots.txt and see if we get something.

Whoa! something is here which is useful.

![3](https://user-images.githubusercontent.com/75982271/110177132-7a44fd80-7e2a-11eb-8c96-56511e3fac6d.png)

We will go inside the root_shell.cgi and check whats inside that.

I found nothing on this page but however we have tracertool and see whats there.

![4](https://user-images.githubusercontent.com/75982271/110177165-88931980-7e2a-11eb-8837-c5d794570d3d.png)


Seems like it will do tracert when we put ip address, Lets put loopback address and see what happens, Sure enough it uses tracert command.

We will try to investigate if we have command injection with ;

![5](https://user-images.githubusercontent.com/75982271/110177218-a2346100-7e2a-11eb-95ab-80116de6e9b2.png)
           

Lets try to get reverse shell with nc and check if that works.

Indeed we got reverse shell


![6](https://user-images.githubusercontent.com/75982271/110177284-c09a5c80-7e2a-11eb-9921-eefd97ecf3d9.png)



I went one folder back and found html folder, Wanted to explore whats inside and ultimately found passwords folder and found one more called FLAG.txt.

In this machine i was not able to use cat command due to which i was using the less command to open the file - FLAG{Yeah d- just don't do it.} - 10 Points

 ![7](https://user-images.githubusercontent.com/75982271/110177356-d6a81d00-7e2a-11eb-881a-dcbcb2db394f.png)


While checking password.html i found a password but however we are not sure whose password is this lets keep in back pocket(This can also be found from gobuster). Password = winter

![8](https://user-images.githubusercontent.com/75982271/110177385-e3c50c00-7e2a-11eb-96d3-ee14b6c32bae.png)


Since we have password lets see if i can cat /etc/passwd file to find the users.

Wow!.. I am able to do it. So we have 3 users RickSanchez, Morty and summer. Lets try to login and see what happens

![9](https://user-images.githubusercontent.com/75982271/110177423-f6d7dc00-7e2a-11eb-8018-75f708d03b6f.png)


I tried RickSanchez and Morty but unfortunately i wasnt able to login. Lets try the last option Summer

![10](https://user-images.githubusercontent.com/75982271/110177460-06572500-7e2b-11eb-9523-6768aaa75ecb.png)


Whoa!. I am able to login to Summer, I should have thought Summer == winter

![11](https://user-images.githubusercontent.com/75982271/110177526-1d961280-7e2b-11eb-8eca-ac9d3dc80f38.png)


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









