# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:
Find out the ip address of the attackers system

## OUTPUT:

![Screenshot 2023-06-11 081442](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/b4069541-3b92-4003-8b62-a8802181e4ba)


Invoke msfconsole:

## OUTPUT:

![Screenshot 2023-06-11 081513](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/329df4fa-d60d-40f0-b73f-99eb08ad34c3)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


![Screenshot 2023-06-11 093844](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/28f8f4e2-1b2b-4f10-a526-f9ac1bbb5de6)


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:


![Screenshot 2023-06-11 081704](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/6ca2d9ae-c61c-4533-95ce-d9ef2861573d)


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:



![Screenshot 2023-06-11 091704](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/9118b2c2-ea43-4b64-bf5e-33616089e9b8)




Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:


![Screenshot 2023-06-11 090040](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/8d6772bb-22fc-48ad-8ca6-bfaa916e8274)




Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit



![Screenshot 2023-06-11 090140](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/1eec15ac-f151-47b2-9b9b-08e4bd115b8f)




The info command provides information regarding a module or platform,

## OUTPUT

![Screenshot 2023-06-11 090643](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/d838ad1b-910b-473b-975c-1beb88a8e608)



Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>



![Screenshot 2023-06-11 091704](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/3f864ba1-c0b9-4568-836b-2d567f63e98f)





Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql


![Screenshot 2023-06-11 090835](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/05deb83c-a488-465e-98ee-83195e163903)





use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version



![Screenshot 2023-06-11 090938](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/88e8cbf7-1d72-4cdd-8fa3-01d5ddf2719a)






Use the set rhosts command to set the parameter and run the module, as follows:


![Screenshot 2023-06-11 091102](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/a3ddcc64-a0b7-4b62-9685-29b0e58fec8f)







After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.


![Screenshot 2023-06-11 091215](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/b0f0a571-a306-4a0f-97d7-4bda19b1676c)









set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true






![Screenshot 2023-06-11 091634](https://github.com/praveenst13/Metasploit-for-reconnaissance/assets/118787793/967aca0b-45b6-4e70-8a06-d611c11b1c0f)











## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
