# notes.txt

## Ubuntu (14)

#### Create user
1. `adduser brad`
2. `gpasswd -a brad sudo`
3. `sudo usermod brad -aG www-data`
4. `su brad`
5. `mkdir ~/.ssh`
6. `vim ~/.ssh/authorized_keys` add key etc.

#### chmod file permissions correctly
- `sudo find /var/www -type d -print -exec chmod 775 {} \;`
- `sudo find /var/www -type f -print -exec chmod 644 {} \;`

## Unload
`sudo chown -R yourname:yourgroup *`


## SSH
`.ssh/config`
```
Host bradleyflood
Hostname bradleyflood.com
User brad
```

### Authorized keys
`chmod 700 ~/.ssh`
`chmod 600 ~/.authorized_keys`

## Upload files from local to remote via SSH
`scp /path/to/image.jpg username@bradleyflood.com:/var/www/bradleyflood.com/html/img/_private`

## Apache (on Ubuntu)
`sudo service apache2 restart`
`a2ensite /etc/apache2/sites-available/bradleyflood.com.conf`
`a2dissite 000-default.conf` etc.

## Terminal

#### Find string in source code
- `curl -v --silent http://www.bradleyflood.com/ 2>&1 | grep 'crazyegg'`

### Curl with headers
- curl https://example.com/ -k -v

### Symlinks
- `ln -s /path/to/source/file /path/and/name/of/symlink`
- Eg `ls -s ~/www/dev/project /MyProjectShortcut`

### Get GZIPed file size in bytes
- `gzip -c path/to/file | wc -c`

## Zip a file
- `zip -r www.zip /var/www`
- `unzip www.zip`

## SSL cert
- `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout ./dev-https.key -out ./dev-https.crt -subj "/CN=local.bradleyflood.com"`


## Git

Enable debug: `export GIT_TRACE=true`

Easily push new branches by:

1. `git config --global push.default current`
2. `git push -u` (or fish `push` by `abbr -a push 'git push -u'` :)

## MYSQL
- `mysql -u db_user -p -h mydb.myaccount.ap-southeast-2.rds.amazonaws.com db_name`
