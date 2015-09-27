# vsftpd server

## Install & configurate

First, install vsftpd server and edit its configuration:

```
$ sudo apt-get install vsftpd
$ sudo gedit /etc/vsftpd.conf</pre>
```

Disable anonymous access, enable local users authentication and upload for local users:
```
...
anonymous_enable=NO
...
local_enable=YES
...
write_enable=YES
...
```

Default umask for local users is 077. Lets change this to 022:

```
...
local_umask=022
...
```

Restart ftp server:

```$ sudo restart vsftpd```

## Create new user

First open `/etc/shells`:

```
$ sudo gedit /etc/shells
```

Add following string to the end:

```
/bin/false
```

Now create home directory for new user:

```
$ sudo mkdir /home/ftp
```

Create usergroup and user (replace `<PASSWORD>` with your password):

```
$ sudo addgroup ftp-users
$ sudo useradd www-user ftp-users
$ sudo useradd ftpuser -g ftp-users -p <PASSWORD> -d /home/ftp -s /bin/false
```

Change the home directory owner and the directory mode:

```
$ sudo chown ftpuser:ftp-users /home/ftp; sudo chmod a-w /home/ftp/
```

Finally, restart ftp server:

```
$ sudo restart vsftpd
```
