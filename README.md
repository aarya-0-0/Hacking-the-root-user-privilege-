# Hacking-the-root-user-privilege

A small project that enables the normal user to get the root privilege. 

**Disclaimer! It is for educational purpose only. This is my experiment on changing user id to gain access to root-user-privilege. This can cause serious errors in the system if not handled in a sandboxed environment. Even while using the a virtual environment, it is recommended to take a snapshot beforehand.

Commands used: 
i. adduser
2. su
3. nano /etc/passwd
4. nano /etc/group

Procedure:
1. Add a user named userA using the adduser command. Set any password then let all the other values be default.
2. We can see, using the cat /etc/passwd command, that the root user has the uid of 0 while userA will always have a uid of 1000-60,000
3. Now, we will edit that file in nano to change the uid of root to a number between 1000-60,000 and the uid of userA will be edited as 0.
4. Make sure both the uid and gid in the /etc/passwd is 0 for userA and root has no 0 in both the id.
5. Also go to change the /etc/group to make it similar to what we did in /etc/passwd
6. Now, switch the user using the command su userA. This switches us to userA.
7. Lastly, run any command without the sudo (superuser do) command

We will notice that the userA now has the root privilege and can even sensitive information like the /etc/shadow file which is for storing passwords.

Conclusion: We can change the root privilege to give it to regular user by only using the text editor to change the uid. A thing to keep in mind is the consequences we will face if the transfer of root privilege to regular user is not accommodated properly.

