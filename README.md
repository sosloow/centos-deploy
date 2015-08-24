## подготовка 64-битной centOS 6 для node.js сервера

1. `useradd someone sudo`
2. `passwd someone`
3. `sudo yum install epel-release`
4. `curl -sL https://rpm.nodesource.com/setup | bash -`
5. `scp ./yum.repos.d/* root@remote:/etc/yum.repos.d`
6. `sudo yum update`
7. `sudo yum install git mongodb-org nodejs nginx`
8. `sudo /sbin/chkconfig --add mongod`
9. `sudo /sbin/chkconfig mongod on`
10. `sudo /sbin/service mongod start`
11. `sudo /sbin/chkconfig --add nginx`
12. `sudo /sbin/chkconfig nginx on`
13. `sudo /sbin/service nginx start`
14. `sudo /sbin/chkconfig httpd off`
15. `sudo /sbin/service httpd stop`
16. `sudo npm install -g forever coffee-script`
17. `scp ./node.conf root@remote:/etc/nginx/conf.d`
