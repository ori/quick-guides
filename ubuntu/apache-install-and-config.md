Install packages from standart repository:

```
$ sudo apt-get install apache2
```

Enable module mod_rewrite:

```
$ sudo a2enmod rewrite; sudo service apache2 restart
```

Add new site with domain `<SITENAME>`:

```
$ sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/<SITENAME>
$ sudo gedit /etc/apache2/sites-available/<SITENAME>
```

In this file replace all `/var/www` to `/home/user/www/<SITENAME>`.

Than insert ServerName `<SITENAME>` above DocumentRoot `/home/user/www/<SITENAME>/` like this:

```
...
ServerName <SITENAME>
DocumentRoot /home/user/www/<SITENAME>/
...
```

Enable Apache site:

```
$ sudo a2ensite <SITENAME>
```

To add host open hosts

```
$ sudo gedit /etc/hosts
```

and insert

```
127.0.1.3 `<SITENAME>`
```

After that reload Apache:

```
$ sudo /etc/init.d/apache2 reload
```
