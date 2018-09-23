title: camel-xquery
date: 2018-09-22 12:43:46
tags:
---
## How to parse message to XQuery's function paramter

By Apache Camel, you could easily pass Xml file to XQuery,
if you XQuery does not have function which takes input message as paramter, you could simply build route like below and it will work.

```
from("file:src/data?moveFailed=.error"). to("xquery:myxquery.xq").to("file:target/output");
```

But if you xquery has its's function which taking input xml message as parameter, then this route will not work, since you need pass xml as message to xquery 

```
declare variable $request as element() external;
return xf:my_xquery_function($request)
```

But you could use $in.body(camel buildi in variable) which mapped to body(message, xml string) to pass it to XQuery's function with a little bit modification as below, and of couse make sure the XQuery version is >=3.0, since parse-xml is function since XQuery3.0

```
declare variable $in.body as xs:string external;
let $request :=parse-xml($in.body)/*
return xf:my_xquery_function($request)
```
Of couse, you also need to convert message from file to Xml String in this case as below shown.

````
from("file:src/data?moveFailed=.error").convertBodyTo(String.class).to("xquery:myxquery.xq").to("file:target/output");
```