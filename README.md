GLASSFISH-18916
===============

[Bug Description]
Create a LifecycleModule,then deploy a application Module that has the same name with the LifecycleModule,NullPointerException happened.

[Operations]
1.create LifecycleModule to the cluster001 : asadmin create-lifecycle-module --target cluster001 --classname aaa hello;

2.deploy the hello.war to the cluster001 : asadmin deploy --force=true --target cluster001 hello.war ,the NullPointerException happened;

-command
remote failure: Error occurred during deployment: Keys cannot be duplicate. Old value of this key property, nullwill be retained. Please see server.log for more details.
java.lang.NullPointerException
Command deploy failed.

-server.log
[#|2012-07-17T14:03:48.000+0800|SEVERE|44.0|javax.enterprise.system.std.com.sun.enterprise.server.logging|_ThreadID=25;_ThreadName=Thread-2;|java.lang.RuntimeException: Error occurred during deployment: Keys cannot be duplicate. Old value of this key property, nullwill be retained. Please see server.log for more details.
java.lang.NullPointerException java.lang.NullPointerException
at org.glassfish.admingui.common.util.RestUtil.parseResponse(RestUtil.java:492)
at org.glassfish.admingui.common.util.RestUtil.restRequest(RestUtil.java:230)
at org.glassfish.admingui.common.util.RestUtil.restRequest(RestUtil.java:156)
......
Caused by: java.lang.RuntimeException: Error occurred during deployment: Keys cannot be duplicate. Old value of this key property, nullwill be retained. Please see server.log for more details.
java.lang.NullPointerException java.lang.NullPointerException
at org.glassfish.admingui.common.util.RestUtil.parseResponse(RestUtil.java:453)
... 52 more

[Affected versions ]
1 4.0_b45
2 gf's trunk until 2012/07/09


 

