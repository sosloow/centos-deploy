## подготовка 64-битной centOS 7 для node.js сервера

1. `useradd user`
2. `passwd user`
4. `curl -sL https://rpm.nodesource.com/setup_6.x | bash -`
5. [подключаем репозиторий mongodb](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/#for-the-latest-stable-release-of-mongodb)
7. `sudo yum install gcc gcc-c++ make openssl-devel git mongodb-org nodejs nginx`
8. `sudo /sbin/chkconfig --add mongod`
9. `sudo /sbin/chkconfig mongod on`
10. `sudo /sbin/service mongod start`
13. `sudo /sbin/service nginx start`
16. `sudo npm install -g pm2 coffee-script bower grunt-cli`
17. `scp ./node.conf root@remote:/etc/nginx/conf.d` (и отредактировать под свои нужды)
19. `sudo firewall-cmd --zone=public --add-port=80/tcp --permanent` (разрешаем и любые другие порты, которые могут понадобиться)
20. `sudo firewall-cmd --reload`
21. [отключаем selinux](http://xmodulo.com/how-to-disable-selinux.html)
22. `pm2 start start path/to/pm2.json`
23. `pm2 save`
24. `sudo PM2_HOME=/home/$(whoami)/.pm2 pm2 startup centos -u $(whoami)`
25. `su -c "chmod +x /etc/init.d/pm2-init.sh; chkconfig --add pm2-init.sh"` (именно под рутом (почему-то))
