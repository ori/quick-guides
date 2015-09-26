Install packages from standart repository:

```
$ sudo apt-get install apache2
```

Enable module mod_rewrite:

```
$ sudo a2enmod rewrite; sudo service apache2 restart
```

Add new site with domain `<sitename>`:

```
$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/<sitename>
$ sudo gedit /etc/apache2/sites-available/<sitename>
```

In this file replace all `/var/www` to `/home/user/www/<sitename>`.

Than insert ServerName `<sitename>` above DocumentRoot `/home/user/www/<sitename>/` like this:

```
...
ServerName <sitename>
DocumentRoot /home/user/www/<sitename>/
...
```

Enable Apache site:

```
$ sudo a2ensite <sitename>
```

To add host open hosts

```
$ sudo gedit /etc/hosts
```

and insert 127.0.1.3 `<sitename>`.

After that reload Apache:

```
$ sudo /etc/init.d/apache2 reload
```
