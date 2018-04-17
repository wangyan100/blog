title: tomcatvps
date: 2017-12-26 11:53:01
tags:
---
# Setup Tomcat+mysql on VPS

I try to host my webapps(tomcat+mysql) on vps (ubuntu), here try to explain steps and solutions for the problem which I come across

# Install tomcat 

 - [Install tomcat8 on ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04)
 
# Install mysql

 - [Install mysql on ubuntu](https://support.rackspace.com/how-to/installing-mysql-server-on-ubuntu/) 

# Using port 80 instead of 8080 for web apps@tomcat
```
[root@myroot ~]# iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080
[root@myroot ~]# iptables -t nat -A PREROUTING -p udp -m udp --dport 80 -j REDIRECT --to-ports 8080
# persist the changes across restarts
sudo apt-get install iptables-persistent

# save for restarts
iptables-save > /etc/iptables/rules.v4
ip6tables-save > /etc/iptables/rules.v6
```

# Fixing No output folder issue
```
Exception

org.apache.jasper.JasperException: java.lang.IllegalStateException: No output folder
    org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:538)
    org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:364)
  org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:313)
  org.apache.jasper.servlet.JspServlet.service(JspServlet.java:260)
  javax.servlet.http.HttpServlet.service(HttpServlet.java:723)
root cause

It is due to write access for left over tomcat\work directory , just remove work directory, it will be re-created again after restarting tomcat

```

### Deploy Application at Tomcat Root

 - [Deploy App at Tomcat Root](http://www.baeldung.com/tomcat-root-application) 
 
  - [Via ROOT.xml](https://stackoverflow.com/questions/7276989/how-to-set-the-context-path-of-a-web-application-in-tomcat-7-0/15625953) 
 
 https://stackoverflow.com/questions/7276989/how-to-set-the-context-path-of-a-web-application-in-tomcat-7-0/15625953