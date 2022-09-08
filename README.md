# tui

import os
import getpass


os.system("tput setaf 1")
print("\t\t\t\t Welcome to TUI console")
os.system("tput setaf 7")
print("\t\t\t\t ----------------------")


passwd = getpass.getpass("Enter your password : ")

apass = "vk"

if passwd != apass:
    print("Invalid Login")
    exit()


print("Enter location to run: local/remote:", end='')
location=input()
print(location)


if location == "remote":
    remoteIP=input("Enter your ip ")
 

while True:
        print("""
        Press1: date
        Press2: cal
        Press3: bc
        Press4: mkdir
        Press5: create user
        Press6: password protect user
        Press7: delete user
        Press8: whatismyip
        Press9: exit
        """
        )   

        print("Enter your choice : ", end="")
        ch=input()
        print(ch)


        if location == "local":
            if int(ch) == 1:
               	os.system('date')
        
            elif int(ch) == 2:
               	os.system('cal')
            elif int(ch) == 3:
               	os.system('bc')
            elif int(ch) == 4:
               	os.system('mkdir')
            elif int(ch) == 5:
               	print("Enter username: " , end='')
       	        create_user = input()
               	os.system("useradd {}".format(create_user))
            elif int(ch) == 6:
               	print("Enter username: " , end='')
       	        passwd_user = input()
               	os.system('passwd {}'.format(passwd_user))
            elif int(ch) == 7:
               	print("Enter username: " , end='')
       	        del_user = input()
               	os.system('userdel {}'.format(del_user))
            elif int(ch) == 8:
               	os.system('ifconfig ens160')
            elif int(ch) == 9:
               	exit()
            else:
               	print("unsupported option")
            input("Enter to continue...")                        
            os.system("clear")                        

        elif location == "remote":
            if int(ch) == 1:
                os.system('ssh {0} date'.format(remoteIP))
            elif int(ch) == 2:
                os.system('ssh {0} cal'.format(remoteIP))
            elif int(ch) == 3:
                os.system('ssh {0} bc'.format(remoteIP))
            elif int(ch) == 4:
                os.system('ssh {0} mkdir'.format(remoteIP))
            elif int(ch) == 5:
                print("Enter username: " , end='')
                create_user = input()
                os.system("ssh {0} useradd {1}".format(remoteIP, create_user))
            elif int(ch) == 6:
                        print("Enter username: " , end='')
                        passwd_user = input()
                        os.system('ssh {0} passwd {1}'.format(remoteIP, passwd_user))
            elif int(ch) == 7:
                        print("Enter username: " , end='')
                        delete_user = input()
                        os.system('ssh {0} userdel {1}'.format(remoteIP, delete_user))
            elif int(ch) == 8:
               	        os.system('ssh {0} ifconfig ens160 '.format(remoteIP))
            elif int(ch) == 9:
                        exit()
            else:
               	print("unsupported option")
            input("Enter to continue...")                        
            os.system("clear")                        
else:
    print('unsupported location')
