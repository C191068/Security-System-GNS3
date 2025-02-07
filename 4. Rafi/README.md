### Hacking Portion of the project <br> <br><br>

Assalamualaikum, I'm Mohammad Rafidul Islam. We are working on a project where we are trying to build a security system on a topology inside GNS3 to protect it from **Cyber Attack**. I have performed the cyber attack portion of the project.<br><br>

I have used Kali Linux for the Cyber Attack.
![1  Kali Linux](https://user-images.githubusercontent.com/120240771/207899133-cdf52c0a-4af3-47e8-a3c7-9dff88113dcf.png)
<br><br>

The software which I have used for the attack is Burp suite community edition. It comes free with Kali Linux
![2  Burp Suite](https://user-images.githubusercontent.com/120240771/207899519-7c0a7e45-9682-4c4f-83e4-aab5fd9825e2.png)
<br><br>

I will go through the initial setup
![3   Bup Suite](https://user-images.githubusercontent.com/120240771/207903083-f13211ef-2f4e-4b35-9896-bbf18a7bf9b5.png)
<br>
![4  Burp Suite](https://user-images.githubusercontent.com/120240771/207903119-c592ad59-676d-4d73-9340-f23929d209f4.png)
<br><br><br>

After finishing up the initial setup we will go to the **Proxy** tab and click the orange **Open Browser** button.
![5  Proxy tab](https://user-images.githubusercontent.com/120240771/207903698-83e195c4-556a-4350-84e6-c486d720ce02.png)
<br><br>

Then a browser will open up, I will then give the address of the Website I want to hack which is **192.168.0.107/cn** in my case. A log in page will appear after giving this address.
![6  Log in](https://user-images.githubusercontent.com/120240771/207904339-16e432d0-a0d6-4962-ba8b-6ffb424d3672.png)
<br><br>

Then I will go to Burp Suite again and click the **Intercept On** button.
![7  Intercept on](https://user-images.githubusercontent.com/120240771/207904717-4711855f-68c5-4206-b387-56e4a6a34df7.png)
<br><br>

Then I will go back to the Log In page and give a legitimate Username and a random password as I don't know it.
![8  Random password](https://user-images.githubusercontent.com/120240771/207905153-36f42732-a807-4919-838c-feb046174370.png)
<br><br>

After that the site will be intercepted by burp suite. Burp suite will come up with the HTML code of the page.
![9  Site intercepted](https://user-images.githubusercontent.com/120240771/207906128-e1c6e5d0-aac2-4001-a5f9-98c81785f2de.png)
<br><br>

Then I will right click and from the options I will select **send to Repeater**. In the Burp Suite the Repeater tab will open with the HTML code of the Log In Page.
![10  Send to repeater](https://user-images.githubusercontent.com/120240771/207907025-f2876578-950b-4066-8058-49f9d91068b6.png)
<br><br>

In the code after password I will give the sql injection code and click the orange button in the upper left corner which says **Send**. But I will get wrong password message in the **Response** tab in the right.
![11  Trying injection](https://user-images.githubusercontent.com/120240771/207907909-69978ea0-42b3-4d29-8d84-14cd775269d4.png)
<br><br>

Since the injection code is not working I will test if the Page is injectable or not. To do that first I will copy the codes from the repeater tab of Burp suite.
![11  Copying the files](https://user-images.githubusercontent.com/120240771/207908377-9f9aa02c-c7a8-405a-bdbc-d011c4332eae.png)
<br><br>

Then I'll create a file named injection and open it with mousepad
![12  Injection file](https://user-images.githubusercontent.com/120240771/207908676-c4c214b6-2826-49dd-9758-aefa45f6aeee.png)
<br><br>

After that I'll paste the copied data in the injection file that I have just created.
![13  Pasting into injection](https://user-images.githubusercontent.com/120240771/207908981-6d9003d6-0c59-4949-a425-b68f665c02a4.png)
<br><br>

Then I'll type the command *"sqlmap -r injection -p username"* to check if the password is injectable. But I found that the username is not injectable.
![14  Testing if injectable](https://user-images.githubusercontent.com/120240771/207910703-51f36bd9-cfae-403b-b2ac-dab9a01961bd.png)
<br><br>

Then I'll type another command *"sqlmap -r injection -p password"* to check if the password is injectable.
![15  Testing if injectable](https://user-images.githubusercontent.com/120240771/207911092-88b296e0-57dd-4f80-8a12-0d292b673aef.png)
<br><br>

But I also found that the password is also not injectable.
![16  Testing if injectable](https://user-images.githubusercontent.com/120240771/207911285-9ae38063-3830-4600-9cb1-77784d08feba.png)
<br><br><br><br>

Since SQL injection attack didn't work next, I'll try brute force attack. In cryptography, a brute-force attack consists of an attacker submitting many passwords or passphrases with the hope of eventually guessing correctly. The attacker systematically checks all possible passwords and passphrases until the correct one is found.

To check all possible passwords we need a wordlist which contains a lot of passwords. Luckily Kali Linux comes with so many wordlists built in. If I go to the directory **/usr/share/wordlists/** I will find all the built in wordlists. From here I will go to the directory **metasploit**<br>
![17](https://user-images.githubusercontent.com/60141836/209540351-063dc63d-2b8c-481c-bdac-54197817c9bb.png)
<br><br>

Then I'll choose the file **unix_passwords.txt**. You can choose the other one as well<br>
![18](https://user-images.githubusercontent.com/60141836/209540354-e744efef-8405-4568-b001-24231408d3cc.png)
<br><br>

Then I'll copy it into the **Documents** folder<br>
![19](https://user-images.githubusercontent.com/60141836/209540355-bfd1c526-bd47-4bd6-b401-a6024a363fce.png)
<br><br>

Then I'll go back to the **Proxy** tab of **Burp Suite** again and **Right Click** then select **Send to Intruder**<br>
![20](https://user-images.githubusercontent.com/60141836/209540306-42b62be6-99ff-4a6e-9c95-37ff9c6dbb1a.png)
<br><br>

In the Intruder tab I'll clear **§** this character from all the lines except from the password<br>
![21](https://user-images.githubusercontent.com/60141836/209540311-f3d4a5b4-b685-4835-a533-b65c14a971af.png)
<br><br>

To clear the character **§** I'll select the line then click the button **Clear §**<br>
![22](https://user-images.githubusercontent.com/60141836/209540313-2d737431-8f3d-4a96-b176-45e4550a8521.png)
<br><br>

Then I'll go to **Payloads** tab and click **Load** in **Payload Options [Simple list]**<br>
![23](https://user-images.githubusercontent.com/60141836/209540314-6061f8bd-1148-4113-a898-be8177f83420.png)
<br><br>

A new window will appear. I'll select the password list that I previously pasted into Documents folder and double click on it<br>
![24](https://user-images.githubusercontent.com/60141836/209540315-5cc4dbd8-d312-4d5a-894f-7374ee6682e0.png)
<br><br>

All the passwords will load into Burp Suite<br>
![25](https://user-images.githubusercontent.com/60141836/209540316-8313a735-fbd6-454c-a0cf-35942dca1470.png)
<br><br>

Then I'll go to the **Options** tab and then into **Grep-Match**<br>
![26](https://user-images.githubusercontent.com/60141836/209540318-61884e7a-b2d3-4766-bf70-0bd095b87009.png)
<br><br>

Then I'll click **Clear** and then **Yes**<br>
![27](https://user-images.githubusercontent.com/60141836/209540322-43abc20a-dc3d-49dd-b04a-1009d90a152d.png)
<br><br>

Then I'll go back to **Repeater** window and copy the error message from the **Response** tab<br>
![28](https://user-images.githubusercontent.com/60141836/209540323-b14fe4ec-bddc-4c3b-8195-5f7db63e9ded.png)
<br><br>

I'll paste the error message into **Grep-Match** in the **Options** window<br>
![29](https://user-images.githubusercontent.com/60141836/209540324-8727becb-b460-4774-8e76-bfa1dc37ee07.png)
<br><br>

Then click **Add**. And check the box where it says **Flag result items with responses**<br>
![30](https://user-images.githubusercontent.com/60141836/209540325-8cb8b32e-74e3-45bf-9b42-4bbef2f956a6.png)
<br><br>

Then click the **Start attack** button on the top right corner of the **Options** window<br>
![31](https://user-images.githubusercontent.com/60141836/209540328-5d9dfd1a-f256-4a20-8b28-c45985a70948.png)
<br><br>

Click **Ok**<br>
![32](https://user-images.githubusercontent.com/60141836/209540330-942aeca1-dcb3-4933-985c-a5aedb2f620f.png)
<br><br>

The attack will start. We can see that status for every try is 200. Which means it is not getting any error. And the value in the __Wrong username & password combination__ is 1. For the correct password it'll 0<br>
![33](https://user-images.githubusercontent.com/60141836/209540333-3abb0ca1-1f3e-4f48-8263-5088da677953.png)
<br><br>

Here we can see that for try 207 the value for __Wrong username & password combination__ is blank or 0. That means this is the correct password<br>
![34](https://user-images.githubusercontent.com/60141836/209540335-ba5bf1fd-bce5-40c2-aede-c740d8f22fc0.png)
<br><br>

Now I'll stop the attack discard it<br>
![35](https://user-images.githubusercontent.com/60141836/209540339-a149c68e-2fc8-4d24-8d8f-6aeb354a7058.png)
<br><br>

And then exit from Burp Suite<br>
![36](https://user-images.githubusercontent.com/60141836/209540343-77bed39f-b65f-4872-b455-b63c17c58a37.png)
<br><br>

Then I'll go to a normal browser give the correct password which I just found out and click **Login**<br>
![37](https://user-images.githubusercontent.com/60141836/209540345-21213f09-0e55-4986-b881-6fcd521b17b7.png)
<br><br>

We can see that the login was successful. Thus it can be said that the Hack was successful<br>
![38](https://user-images.githubusercontent.com/60141836/209540348-8dedac8a-ff91-497c-84fb-e28a47f38f47.png)
<br><br>