# Error Log Overview

But those are not activated by default, there's two places to see error log: **at the server side** and **at the client side**.
The php errors are generally at the server side, and js error are generally at the client side, with some exceptions that are at server side.

* [Error Log at Client side](#error-log-at-client-side)
* [Error Log at Server side](#error-log-at-server-side)

## Error Log at Client side

Depends totally of the browser, mostly firefox/palemoon the officially supported or those _webkit_ based (chromium/chrome, qupzilla, etc by example).

1. After loading the page, hit the F12 key
2. the scree will split in two parts, that second new part its the web-browser devel tool
3. that second part has a "netwok" tab, go/hit in that network tab
4. all the web traffic to the ospos will be displayed, all the request and response
5. each request will have a line entry and also same for each response

![hot F12 at the web browser and see the new split window](https://github.com/venenux/osposos/raw/master/debianOspos/screenshot-ospos-devel-f12-client-log-error.png)

## Error Log at Server side

Here are varios components in action, in first place there's the application log (disabled by default) and the system components log (apache log that includes php error log, database error log), lest see how to enabled/activate those:

In standar distributions if you can access server files or have setup a local installation, a general file that will register all error happened to php script procesing will be always present. 

* In standar Server or Linux installations that file will be under `/var/log/<WEBSERVERNAME>/error.log` 
* In standar binaries of apache2 instalations that file will be under `${INSTALL_DIR}/logs/error.log`
* In standar binaries of nginx/lightttpd/otyhers that files will be also under `${INSTALL_DIR}/logs/error.log`

By example, you can customize that in the apache2.conf or http.conf file configuration of the apache2 webserver with those directives:

```
ErrorLog "${INSTALL_DIR}/logs/apache_error.log"
CustomLog "${INSTALL_DIR}/logs/access.log" common
```

**IMPORTANT** Please refers to the web server documentation to customize that..

