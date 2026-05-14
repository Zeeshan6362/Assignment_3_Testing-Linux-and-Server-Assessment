# Assignment_3_Testing-Linux-and-Server-Assessment

Question #1:
zeeshanshaikh@ZeeshansMacBook ~ % mkdir -p webapp/{scripts,logs,config}

zeeshanshaikh@ZeeshansMacBook ~ % cd webapp

zeeshanshaikh@ZeeshansMacBook webapp % ls
config	logs	scripts

zeeshanshaikh@ZeeshansMacBook webapp % cd ~

zeeshanshaikh@ZeeshansMacBook ~ % cat > webapp/config/app.conf
APP_NAME=WebApp
PORT=8080

zeeshanshaikh@ZeeshansMacBook ~ % touch webapp/logs/app.log

zeeshanshaikh@ZeeshansMacBook ~ % ls -l webapp/logs/app.log
-rw-r--r--  1 zeeshanshaikh  staff  0 14 May 18:13 webapp/logs/app.log

zeeshanshaikh@ZeeshansMacBook ~ % chmod 755 webapp/scripts

zeeshanshaikh@ZeeshansMacBook ~ % chmod 644 webapp/config/app.conf

zeeshanshaikh@ZeeshansMacBook ~ % sudo chown -R root:root webapp/
Password:
chown: root: illegal group name

zeeshanshaikh@ZeeshansMacBook ~ % sudo chown -R root:wheel webapp/

zeeshanshaikh@ZeeshansMacBook ~ % ls -lR webapp/
total 0
drwxr-xr-x  3 root  wheel  96 14 May 18:13 config
drwxr-xr-x  3 root  wheel  96 14 May 18:13 logs
drwxr-xr-x  2 root  wheel  64 14 May 18:12 scripts

webapp//config:
total 0
-rw-r--r--  1 root  wheel  0 14 May 18:13 app.conf

webapp//logs:
total 0
-rw-r--r--  1 root  wheel  0 14 May 18:13 app.log

webapp//scripts:
total 0
zeeshanshaikh@ZeeshansMacBook ~  %


<img width="1637" height="1024" alt="Screenshot 2026-05-14 at 9 46 48 PM" src="https://github.com/user-attachments/assets/b8a8bb0c-ea89-4812-b46d-a43f4f7d52b1" />

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Question #2:

zeeshanshaikh@ZeeshansMacBook ~ % sudo vim webapp/scripts/log_user.sh

##In the editor, entered the command:
#!/bin/bash
read -p "Enter your name: " username
cat webapp/config/app.conf
echo "Login: $username Date: $(date)" >> webapp/logs/app.log
cat webapp/logs/app.log


zeeshanshaikh@ZeeshansMacBook ~ % sudo chmod +x webapp/scripts/log_user.sh
zeeshanshaikh@ZeeshansMacBook ~ % sudo ./webapp/scripts/log_user.sh
Enter your name: Zeeshan
Login: Zeeshan Date: Thu May 14 18:20:16 IST 2026

zeeshanshaikh@ZeeshansMacBook ~ % sudo ./webapp/scripts/log_user.sh
Enter your name: Rajan
Login: Zeeshan Date: Thu May 14 18:20:16 IST 2026
Login: Rajan Date: Thu May 14 18:20:28 IST 2026

zeeshanshaikh@ZeeshansMacBook ~ % sudo ./webapp/scripts/log_user.sh
Enter your name: Chirag
Login: Zeeshan Date: Thu May 14 18:20:16 IST 2026
Login: Rajan Date: Thu May 14 18:20:28 IST 2026
Login: Chirag Date: Thu May 14 18:20:35 IST 2026

zeeshanshaikh@ZeeshansMacBook ~ % zeeshanshaikh@ZeeshansMacBook ~ % cat webapp/logs/app.log          
Login: Zeeshan Date: Thu May 14 18:20:16 IST 2026
Login: Rajan Date: Thu May 14 18:20:28 IST 2026
Login: Chirag Date: Thu May 14 18:20:35 IST 2026
zeeshanshaikh@ZeeshansMacBook ~ % 


<img width="1637" height="1024" alt="Screenshot 2026-05-14 at 9 46 48 PM" src="https://github.com/user-attachments/assets/3768b0bd-02d9-4482-b877-8686584dc64c" />
<img width="1637" height="1024" alt="Screenshot 2026-05-14 at 9 46 46 PM" src="https://github.com/user-attachments/assets/779de586-0680-473e-a34e-6c9631d4b076" />
<img width="1637" height="1024" alt="Screenshot 2026-05-14 at 6 19 07 PM" src="https://github.com/user-attachments/assets/13746207-bb67-4204-a13d-1b6d42d5fdcf" />
<img width="1637" height="1024" alt="Screenshot 2026-05-14 at 9 46 43 PM" src="https://github.com/user-attachments/assets/3b6339a7-c617-4a63-8f11-318ab751cdd2" />

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Question #3: 

# As Mac terminal did not support the linux commands for this section, I completed this section in KLLRCODA and pasted all the commands below

sudo groupadd writers
sudo useradd -m devuser1
sudo useradd -m devuser2
sudo useradd -m devuser3
sudo useradd -m devuser4

sudo usermod -aG writers devuser1
sudo usermod -aG writers devuser2

sudo chown root:writers /home/ubuntu/webapp/scripts/log_user.sh

sudo chmod 664 /home/ubuntu/webapp/scripts/log_user.sh
ls -l webapp/scripts/log_user.sh

sudo su - devuser1
echo "# test comment" >> /home/ubuntu/webapp/scripts/log_user.sh
exit

sudo su - devuser3
echo "Login: devuser3 Date: $(date)" >> /path/to/webapp/scripts/log_user.sh
cat /path/to/webapp/scripts/log_user.sh
exit

