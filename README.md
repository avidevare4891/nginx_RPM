# nginx_RPM
RPM POC STEPS 
 1. Install required yum dependencies <br/>
    - Creating the build server 
    -  Following package need to install  for package creation  <br/>
       $ sudo yum install -y git wget make \
       gcc rpm-build GeoIP-devel zlib-devel \
       pcre-devel gd-devel libedit-devel which \
       perl-devel perl-ExtUtils-Embed libxslt-devel \
       openssl-devel

2.Import the nginx source code

$ git clone https://nginx.googlesource.com/nginx-pkgoss <br/>
$ cd nginx-pkgoss <br/>
$ git checkout nginx-1.19.8 <br/>

3.Required modification <br/>
 &nbsp;&nbsp;&nbsp; Following changes are expected <br/>
 &nbsp;&nbsp; &nbsp;1.Modify the “nginx” user to “myuser”<br/>
 &nbsp;&nbsp;&nbsp; 2.Modifying  the error log locations from  <br/>
 &nbsp;&nbsp;&nbsp; “/var/log/nginx/error.log”  to  “ /var/log/nginx/error/error.log” <br/>
 &nbsp;&nbsp;&nbsp; 3.Attaching the diff file whatever changes has been done in source code <br/>
<br/>
4.Run make command to build all modules <br/>
$ cd rpm/SPECS/ <br/>
$ make all <br/>
<br/>
5. The built rpm packages following location <br/>
$ cd $HOME/nginx-pkgoss/rpm/RPMS/x86_64 <br/>
<br/>
6. Install the built nginx rpm <br/>
$ sudo rpm -i nginx-1.19.8-1.el7.ngx.x86_64.rpm <br/>
<br/>
7. Check nginx is installed and is available for use <br/>
$ nginx -V <br/>
<br/>
8. Start nginx services <br/>
$ sudo systemctl start nginx <br/>
<br/>
9. Check to ensure that nginx is working and is in running state <br/>
$ sudo systemctl status nginx <br/>
<br/>
10.Verfiy the username for nginx process <br/>
 $  ps -aux | grep nginx <br/>
 <br/>
11.Verify the path for error log path <br/>
  $  cd /var/log/nginx/error/ <br/>
 <br/>
12.Verify the username and error.log file path nginx.conf file <br/>
  $  cat /etc/nginx/nginx.conf <br/>
 






















