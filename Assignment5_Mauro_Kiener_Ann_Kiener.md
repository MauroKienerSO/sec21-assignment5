# Assignment 5 - Security 

## Mauro Kiener, Ann Kiener

## Secure E-Mail Server

### Commands

*Install the Mail Transfer Agent  Exim 4 and the Mail user Agent Mutt*
<br>
<font color='green'>sudo apt update</font>
<br>
<font color='green'>sudo DEBIAN_PRIORITY=low apt install mutt exim4 exim4-daemon-heavy</font>

*Modify zone file*
<br>
<font color='green'>sudo vim /var/lib/knot/zones/kiener.sec21.zone</font>

*Restart Knot*
<br>
<font color='green'>sudo systemctl restart knot</font>

*Start Exim 4*
<br>
<font color='green'>sudo service exim4 start</font>

*Open Mutt and send Test Mail*
<br>
<font color='green'>sudo mutt -s "Test Mail" ann.kiener@students.unibe.ch</font>

*Installing Dovecot*
<br>
<font color='green'>sudo apt install dovecot-core dovecot-imapd dovecot-sqlite</font>

*Installing RoundCube*
<br>
<font color='green'>sudo apt install roundcube-sqlite3 roundcube php-fpm</font><br>
<font color='green'>sudo systemctl enable php7.4-fpm</font><br>
<font color='green'>sudo systemctl start php7.4-fpm</font><br>

*Update NGINX configuration*<br>
<font color='green'>sudo vim /etc/nginx/sites-available/kiener.sec21.tech.conf</font><br>

*Reload NGINX*<br>
<font color='green'>sudo systemctl restart nginx</font><br>

*Change Password for ubuntu user*<br>
<font color='green'>sudo passwd ubuntu</font><br>

*Update Roundcube config*<br>
<font color='green'>sudo vim /etc/roundcube/config.inc.php</font><br>

*Create Certificate for mail Server (configure for mail.kiener.sec21.tech)*<br>
<font color='green'>sudo certbot certonly</font><br>

*Update Exim Conf (add ports)*<br>
<font color='green'>sudo vim /etc/default/exim4</font><br>

*Update Exim Conf (configure TLS)*<br>
<font color='green'>sudo vim /etc/exim4/exim4.conf.template</font><br>

*Reload exim4*<br>
<font color='green'>sudo service exim4 restart</font><br>

*Update IMAP Server conf (dovecot, set SSL required)*<br>
<font color='green'>sudo vim /etc/dovecot/conf.d/10-ssl.conf</font><br>
<font color='green'>sudo service dovecot reload</font><br>

*Update Exim and Dovecot conf*<br>
<font color='green'>sudo vim /etc/exim4/exim4.conf.template</font><br>
<font color='green'>sudo vim /etc/dovecot/conf.d/10-master.conf</font><br>
<font color='green'>sudo vim /etc/dovecot/conf.d/10-auth.conf</font><br>
<font color='green'>sudo service dovecot reload</font><br>
<font color='green'>sudo service exim4 restart</font><br>
