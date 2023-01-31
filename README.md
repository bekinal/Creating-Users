<h1>Creating Users</h1>

<h2>Description</h2>
Project consists of creating new users and configuring customized home directories and password policies.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b>
- <b>Debian Environment</b>
- <b>Terminal</b>

<h2>Modifying password length/ crating and modifying new users:</h2>
The su and nano commands will be used to change the minimum required password length to eight characters for new users. This configuration is then used to create and modify new users. First, the root account is accessed running the su command. Note that it is not recommended to work with the root account, I will just be using it for this project:<br/>
<img src="https://imagizer.imageshack.com/img923/4917/SJzAA4.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The common-password file is opened using the nano command:<br/>
<img src="https://imagizer.imageshack.com/img923/9749/aKfu95.png" alt="Disk Sanitization Steps"/>
<br />
<br />
Scrolling down, the option "password [success=1 default=ignore] pam_unix.so obscure sha512" is navigated to. The text string "minlen=8" is added to this line. This will change the password requirement to eight characters:<br/>
<img src="https://imagizer.imageshack.com/img923/1958/hpM8Ig.png" alt="Disk Sanitization Steps"/>
<br />
<br />
Changes are saved with Ctrl + o. Ctrl + x is used to exit the file:<br/>
<img src="https://imagizer.imageshack.com/img923/9849/X1rxqE.png" alt="Disk Sanitization Steps"/>
<br />
<br />
A folder named template is created under /etc/skel with the mkdir command:<br/>
<img src="https://imagizer.imageshack.com/img922/2520/Iuhu6z.png" alt="Disk Sanitization Steps"/>
<br />
<br />
A new user jane is added using the adduser command. A password shorter than 8 characters is defined (this works due to root permissions) to portray our new password policy later on:<br/>
<img src="https://imagizer.imageshack.com/img922/9839/SNEOyT.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The jane user is then switched to using su. The ls command provides that the template directory is within janes home directory:<br/>
<img src="https://imagizer.imageshack.com/img923/4540/szOqLJ.png" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, attempting to change the password to something shorter than 8 characters will prompt an error message:<br/>
<img src="https://imagizer.imageshack.com/img924/1797/qnIyUI.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The root user is switched to by using the exit command:<br/>
<img src="https://imagizer.imageshack.com/img924/4021/Y5POMT.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The /etc/passwd file is then opened using nano:<br/>
<img src="https://imagizer.imageshack.com/img924/16/5H0uXD.png" alt="Disk Sanitization Steps"/>
<br />
<br />
At the bottom, the following line is added as a test:<br/>
<img src="https://imagizer.imageshack.com/img923/5595/Wf0jRS.png" alt="Disk Sanitization Steps"/>
<br />
<br />
To create a user without the adduser command, a password is set for the user with the passwd <name> command:<br/>
<img src="https://imagizer.imageshack.com/img922/337/loIl2r.png" alt="Disk Sanitization Steps"/>
<br />
<br />
The integrity of the file is then checked using the pwck command. pwck creates an alert that the new user is missing a corresponding group, home directory, and password entry in the shadow file, but it will not notice that it was added incorrectly:<br/>
<img src="https://imagizer.imageshack.com/img922/2057/yogYrM.png" alt="Disk Sanitization Steps"/>
<br />
<br />


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
