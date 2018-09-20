title: How to use log4j2
date: 2018-09-17 10:19:32
tags:
---
## Log4j2 is very powerful logging framework, here shows you how to use some of most important features

- Daily File Rolling
- Compressing log file to gz format
- Set Max backup file numbers
- Using Lambda Expression in log to improve performance



Daily File Rolling, compressing log file,  backup file numbers are very important for logging , unfortunately the old logging frameworks did not support them well, we even have to use cron job to do those tasks . Now with log4j2, it supports all those features even with Lambda expression.

I will use some examples to show you how to do those things.



Firstly you need to add dependency for Log4j2 in your project, below is example with maven
![dependencies](/2018/09/17/How-to-use-log4j2/screenshot/dependencies.PNG?classes=float-left)
  
Line 6, 12 are for console and file appenders,  Line 14 and 21 are for log file's daily file rolling and file compressing format, Line 23 is for log file max backup numbers

  ![dependencies](/2018/09/17/How-to-use-log4j2/screenshot/log4j2.PNG)

Below example is for customizing log4j2 config file's location and name, if the config file's name is not default, for example, log4j2.xml, and not in classpath. You could use system.setProperty to give customized value.

Another very useful feature of Log4j2 is to support Lambda expression. By using it, you could improve performance by lazy logging.

Without Lambda , you have to always call isTraceEnabled , then build you logs in extra method getRandomNumber()


 ![dependencies](/2018/09/17/How-to-use-log4j2/screenshot/locationandlambda.PNG)
 
 ```
 if (logger.isTraceEnabled()) {
    logger.trace("Number is {}", getRandomNumer());
}

```
With Lambda, you could avoid this, and also can write what getRandomNoumber method does in Lambda expression to improve performance and make your code tidy
```
logger.trace("Number is {}", () -> getRandomNumber());
```
or

```
logger.trace("Number is {}", () -> { 
	Random rand = new Random(); 
	return rand.nextInt(50) + 1;
});
```