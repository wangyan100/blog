title: How to use log4j2
date: 2018-09-17 10:19:32
tags:
---
## Log4j2 is very powerful logging framework, I will show you how to use some of most important features 



- to use it, you have to add dependencies 
![dependencies](/2018/09/17/How-to-use-log4j2/screenshot/dependencies.PNG?classes=float-left)
  
- setting for daily file rolling, compressing log files to gz format, max backup file numbers as 30 files, using console and file appenders, and setting log level on package and root level 

  ![dependencies](/2018/09/17/How-to-use-log4j2/screenshot/log4j2.PNG)

- Customizing location and name of log4j2.xml,if it is not default, and using lambda experssion in your log

 ![dependencies](/2018/09/17/How-to-use-log4j2/screenshot/locationandlambda.PNG)