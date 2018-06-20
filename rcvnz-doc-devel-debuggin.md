# Error Log Overview

There's two places to see error log: **at the server side** and **at the client side**. 
The php errors are generally at the server side, and js error are generally at the client side, 
with some exceptions like ajax and jquery that are also at server side.

About php, there are two aspects to it.  The first is identifying where the log is to be created and the second is establishing what should be written to the log. If the error is due to something going haywire in the application code then you might need to activate the PHP error log in configuration and also in the application config files.

The PHP configuration file (php.ini) is used to describe the error log.   The php.ini file is typically found in the root folder of the PHP installation, however it doesn't have to be located there (as described on page http://php.net/manual/en/configuration.file.php). The php ini files in modern instalations set error log path to emnpty value so will be managed by the webserver, for toher you must consult the php proper documentation of each binary distribution.

# Errors management and configurations

* [Error Log at Client side](#error-log-at-client-side)
* [Error Log at Server side](#error-log-at-server-side)
  * [Application error log, db error log, etc](#application-error-log)
  * [WebServer error log, php errors, etc](#webserver-error-log)

## Error Log at Client side

Depends totally of the browser, mostly firefox/palemoon are recomended, chromium/chrome has good tools but 
standars in that _webkit_ based (chromium/chrome, qupzilla, etc by example) are not well handled.

1. After loading the page, hit the F12 key
2. the scree will split in two parts, that second new part its the web-browser devel tool
3. that second part has a "netwok" tab, go/hit in that network tab
4. all the web traffic to the ospos will be displayed, all the request and response
5. each request will have a line entry and also same for each response
6. can you see those that are not 200 or 303 and also for invalid data in 

![hot F12 at the web browser and see the new split window](rcvnz-doc-devel-debuggin-screenshot01.gif)

## Error Log at Server side

Here are varios components in action, in first place there's the application log debug level (disabled by default) 
and the system components log (apache log that includes php error log, database error log), 
lest see how to enabled/activate those:

### WebServer error log:

Always active, in standar distributions if you can access server files or have setup a local installation, 
a general file that will register all error happened to php script procesing will be always present. 

* In standar Server or Linux installations that file will be under `/var/log/<WEBSERVERNAME>/error.log` 
* In standar binaries of apache/nginx/lightttpd that files will be also under `${INSTALL_DIR}/logs/error.log`

**IMPORTANT** Please refers to the web server documentation to customize that..

### Application error log:

It's disabled by default, since 3.1 OSPOS, can be enabled in a directive in `config/defaults.php.inc` named `$config['debug_level'] = 1;` that are set to `1` by default, set to `4` to enable debug huge log, **for reporting and submit issues please set to `4` and attach only relevant part. will default the location of the results logs at `logs/`, please take in consideration that since RC 1.1 the entry in `config/defaults.php.inc` must ber copy to the configuration file of site.

#### Database SQL Logging

It's disabled and can be enabled in a directive in `config/defaults.php.inc` named `$config['sql_debug'] = true; ` that are set to `FALSE` by default, set to TRUE to enable. Will default the location of the results logs in the same log file of application at `logs/`. Please take in consideration that since RC 1.1 the entry in `config/defaults.php.inc` must ber copy to the configuration file of site.
  
### WebServer error log:

In standar distributions if you can access server files or have setup a local installation, 
a general file that will register all error happened to php script procesing will be always present. 

* In standar Server or Linux installations that file will be under `/var/log/<WEBSERVERNAME>/error.log` 
* In standar binaries of apache/nginx/lightttpd that files will be also under `${INSTALL_DIR}/logs/error.log`

**IMPORTANT** Please refers to the web server documentation to customize that..
