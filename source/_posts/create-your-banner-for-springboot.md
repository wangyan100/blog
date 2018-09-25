title: create your banner for springboot
date: 2018-09-25 16:08:56
tags:
---
# How to change SpringBoot banner



The default banner of springboot is like below shown, you could use new text and new picture to replace default banner.  

### Why we need it? 

You can use this feature to customize your own banner and increase your team's recognition of your own brand or product.

### default banner

 ![default banner](/2018/09/25/create-your-banner-for-springboot/images/origbanner.PNG)




### new banner

![new banner](/2018/09/25/create-your-banner-for-springboot/images/newbanner.PNG)



### How to do this? 

- put your the new banner.txt into resources directory

- put your the new banner image into resource directory or via  below settings in application.properties

 ```
  spring.banner.location=classpath:/path/to/banner/bannername.txt 
  spring.banner.image.location=classpath:banner.gif
  spring.banner.image.width=  //TODO
  spring.banner.image.height= //TODO
  spring.banner.image.margin= //TODO
  spring.banner.image.invert= //TODO
 ```

- restart the application

