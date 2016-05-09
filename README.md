## подготовка 64-битной centOS 7 для node.js сервера

1. `useradd user`
2. `passwd user`
4. `curl -sL https://rpm.nodesource.com/setup_6.x | bash -`
7. `sudo yum install gcc gcc-c++ make openssl-devel git mongodb-org nodejs nginx`
8. `sudo /sbin/chkconfig --add mongod`
9. `sudo /sbin/chkconfig mongod on`
10. `sudo /sbin/service mongod start`
13. `sudo /sbin/service nginx start`
16. `sudo npm install -g pm2 coffee-script bower grunt-cli`
17. `scp ./node.conf root@remote:/etc/nginx/conf.d`
19. `sudo firewall-cmd --zone=public --add-port=80/tcp --permanent`
20. `sudo firewall-cmd --reload`
21. `sudo setenforce 0`
