sTo enable ssh for a user edit the ssh config file at:

`/etc/ssh/sshd_config`

Add or modify the following line:

`AllowUsers     userName`

- make sure to follow AllowUsers by a tab and then the username

restart the ssh service:
`sudo systemctl restart sshd`

#linux #enablessh #sshconfig #ssh 
