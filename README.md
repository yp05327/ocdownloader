# ocDownloader for nextcloud
I'm using nextcloud and found no download apps.Then I found this app, but it's for owncloud and the author's website is 404 now.It's bad.  
So I fork the project and made some changes to let it work in nextcloud.

# Install
## ARIA2 installation
1. install aria2:  
```
sudo apt-get install aria2
```

2. I use supervisor(needs python) to run aira2
Take care: whatever you use, you should run aira2 by user www-data. 

This is my config of supervisor:  
```
[program:aria2-ocdownloader]
command=/usr/bin/aria2c --enable-rpc --rpc-allow-origin-all -c -D --check-certificate=false
autostart=true
autorestart=true
user=www-data
```

3. use 'ps -aux | grep aria2c' to check whether aira2c is running by user www-data. 

## YouTube-DL
I can't use YouTube in China so I have not installed. 

## ocdownloader
1. copy whole files to apps.
2. Download [jquery.iframe-transport.js](https://github.com/cmlenz/jquery-iframe-transport)  
copy jquery.iframe-transport.js to /apps/files/js/jquery.iframe-transport.js
3. edit config/config.php, add
```
'filesystem_check_changes' => 1,
```
This setting will autorefresh contents when you visit. If you not setting to 1, when you have finished downloading bt, you can't see the files, but on server they are there.
4. give the permisson to user www-data.

```
chown -R www-data:www-data /where your nextcloud is/
```



