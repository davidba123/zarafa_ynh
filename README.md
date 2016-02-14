# zarafa_ynh
Zarafa WebApp for YunoHost

# Setup
Currently YunoHost does not offer any automatic way to setup mail transports and therefore enable mail delivery to any mailserver besides the pre installed Dovecot. To be able to recieve mails the following steps have to be taken:

## Enable transport maps in Postfix
To be able to manually define transports in Postfix the following line has to be added to the **main.cf** file of Postfix:
```transport_maps = hash:/etc/postfix/transport```
After adding this line Postfix has to be restarted.

## Define transports
For each user that should receive his or her mail in Zarafa the following line has to be added to **/etc/postfix/transport** (you have to create the file if it does not exist):
```
email-of-user@yunohost-domain.org lmtp:127.0.0.1:2003
```
After each change to this file you have to execute the following command to activate the change:
```
sudo postmap /etc/postfix/transport
```
