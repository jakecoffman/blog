---
title: Guacamole Client ported to Go
date: 2020-01-19T14:29:28-06:00
tags: [programming]
---

I was able to open source some work I did at [WWT](https://wwt.com) recently. It is a port of the Apache Guacamole Client to Go: https://github.com/wwt/guac

The Apache Guacamole project describes itself better than I could:

> Apache Guacamole is a clientless remote desktop gateway. It supports standard protocols like VNC, RDP, and SSH. We call it clientless because no plugins or client software are required. Thanks to HTML5, once Guacamole is installed on a server, all you need to access your desktops is a web browser.

I ported the client from Java to Go. The client sits between `guacd` and the JavaScript app. The main motivation for this was Go is easier to work with than the old Java servlet setup that the Apache project uses.

I also created a simple SPA example using Vue: https://github.com/wwt/guac-vue.

The official project uses the old AngularJS 1.X so I thought a nice Vue example would be good to have on hand.

Here's a little demo:

![Guac demo](/blog/guac.gif)
