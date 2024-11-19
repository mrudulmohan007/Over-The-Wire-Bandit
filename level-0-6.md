LEVEL-0-----------------------------------------
Bandit Level 0
Level Goal
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. 
The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.
ans--> echo bandit0>0; sshpass -p $(cat 0) ssh bandit0@bandit.labs.overthewire.org -p 2220
Once we are in the bandit0 server, type #cat readme and copy the password and after exiting from the bandit server, save it in a file named 1
 by the command #echo "password">1

Bandit Level0→Level 1--------------------------------------------------------------------------------------------------------------------

Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. 
Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

solution--> sshpass -p $(cat 1) ssh bandit1@bandit.labs.overthewire.org -p 2220 to enter into bandit1 server

Bandit Level 1→ Level 2----------------------------------------------------------------------------------------------------------------------

Level Goal
The password for the next level is stored in a file called - located in the home directory

solution--> we are in bandit1 server,
#ls
#cat ./- to read the file and copy the password and exit out of the server and in our machine do:  #echo "password copied" >2
 #sshpass -p $(cat 2) ssh bandit2@bandit.labs.overthewire.org -p 2220 to enter into bandit2 server
 
Bandit Level 2 → Level 3-----------------------------------------------------------------------------------------------------------------------
Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory
Solution:--> #ls and the result will be spaces in this filename
To read such file do , #cat spaces\ in\ this\ filename  and copy the password and exit out of the bandit2 server.
and do #echo "password copied" > 3
#sshpass -p $(cat 3) ssh bandit3@bandit.labs.overthewire.org -p 2220 to enter into bandit3 server

Bandit Level 3 → Level 4-------------------------------------------------------------------------------------------------------------------------
Level Goal
The password for the next level is stored in a hidden file in the inhere directory.
#cd inhere/
#ls -a will show the hidden files
#cat .hidden and copy the password and exit outof the server and do #echo "password copied" > 4
#sshpass -p $(cat 4) ssh bandit4@bandit.labs.overthewire.org -p 2220 to enter into bandit4 server

Bandit Level 4 → Level 5--------------------------------------------------------------------------------------------------------------------------
Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. 
Tip: if your terminal is messed up, try the “reset” command.
Solution--> #ls, #cd inhere/
#ls will list files which starts with -, there will be a lot of files like this.
To check the filetype of a file, eg: file ./file01
our intention is to find the only human-readable file in the inhere directory.
For that we will loop through the listed files and check the condition
To do so, we will do #for i in $(ls); do file ./$i; done, results will give the ascii text type file, in my case it is-file07.
cat ./-file07 and copy the password and exit out of the server
#echo "password copied">5
#sshpass -p $(cat 5) ssh bandit5@bandit.labs.overthewire.org -p 2220 to enter into bandit5 server

Bandit Level 5 → Level 6----------------------------------------------------------------------------------------------------------------------------
Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

Solution---> #cd inhere/
#ls will list a lot of directories
To list the files inside all the directories in one go, do #ls -alR
so we can manually look and search the size of the file and do a for loop to find if the file is readable or not.
But we need another simpler way, for that we use the command #find . -readable -size 1033c -not -executable, 
then we will get the file name and we should cat the file name to get the password and copy it right away and then exit outof the server
#echo "password copied" >6
#sshpass -p $(cat 6) ssh bandit6@bandit.labs.overthewire.org -p 2220 to enter into bandit6 server