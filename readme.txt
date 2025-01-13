This Repository offers all necessary files to reproduce the attacks demonstrated in my paper "Insecure by Design: A Practical Analysis of MQTT Security Risks and Attacks".

1. Before trying to replicate the attacks, make sure you have Docker, Wireshark and htop installed. This can be done in a bash with "apt install Wireshark" for example. If this doesn't work, there are plenty of tutorials online. 
2. To configure broker properties, edit the "docker-compose" file.
	-You can add new users and passwords under "entrypoint"
	-To edit the connect and publish frequencies, edit "sleep" under "entrypoint" to the desired value
3. To start the Docker containers, navigate to the directory of the "unencrypted" folder and use the command "sudo docker compose up"
4. Use "sudo Wireshark" and "sudo htop" to start the corresponding applications
5. The following commands have been used for my attacks:
	-Unencrypted Communication: Navigate to the "encrypted CPU Exhaust" Folder. Start the Docker Containers via "sudo docker compose up". A docker container has been set up 	to automatically connect and publish information every 20 seconds after start up. Simply track packages in Wireshark.
	-Denial of Service: First start htop to monitor the CPU usage prior to the attack. Navigate to the "unencrypted SSL Attack" folder and run "sudo docker compose up".
	Then open a second bash to run the following command: openssl s_client -connect localhost:1883
	-CPU exhaustion should now be visible at 100% in htop
