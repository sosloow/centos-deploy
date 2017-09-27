## подготовка 64-битной centOS 7 для node.js сервера

1. `useradd user -G wheel`
2. `passwd user`
4. `curl -sL https://rpm.nodesource.com/setup_8.x | bash -`
5. [подключаем репозиторий mongodb](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/#for-the-latest-stable-release-of-mongodb)
6. [ставим redis](http://sharadchhetri.com/2014/10/04/install-redis-server-centos-7-rhel-7/)
7. `sudo yum install -y epel-release gcc gcc-c++ make openssl-devel git mongodb-org nodejs nginx ImageMagick ImageMagick-devel redis certbot-nginx`
9. `sudo systemctl start mongod.service`
10. `sudo systemctl enable mongod.service`
11. `sudo systemctl start redis.service`
12. `sudo systemctl enable redis.service`
13. `sudo systemctl start nginx.service`
14. `sudo systemctl enable nginx.service`
16. `sudo npm install -g pm2`
17. `scp ./node.conf root@remote:/etc/nginx/conf.d` (и отредактировать под свои нужды)
17. `sudo certbot --nginx -d example.com` (генерим сертификаты ssl для домена и правим кофиги nginx)
18. `systemctl enable firewalld` (включаем фаервол)
19. `sudo firewall-cmd --zone=public --add-port=443/tcp --permanent` (разрешаем и любые другие порты, которые могут понадобиться)
20. `sudo firewall-cmd --reload`
21. [отключаем selinux](http://xmodulo.com/how-to-disable-selinux.html)
22. `pm2 start path/to/pm2.json`
23. `pm2 save`
24. `sudo PM2_HOME=/home/$(whoami)/.pm2 pm2 startup centos -u $(whoami)`
25. `su -c "chmod +x /etc/init.d/pm2-init.sh; chkconfig --add pm2-init.sh"`
26. настройка бекапов монго: нужно скопировать файл `automongobackup.sh` в `/etc/cron.daily`. Если требуется отправка отчетов на почту, нужно поставить почтовую программу (`sudo yum install mailx`) и указать свой имейл в файле скрипта
