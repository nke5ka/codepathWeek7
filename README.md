# codepathWeek7
For Network Security course at UVA.

## WordPress v2.5 to v4.6 - Authenticated Stored Cross-Site Scripting via Image Filename (CVE-2016-7168)
First step of this is social engineering - sending the admin a file that they would upload to the wordpress site.  The file is a trap, however!  The image is titled `dogsocute<img src=a onerror=alert("HACKED!!!")>.png` and when uploaded to the WP site will execute javascript!

![](https://github.com/nke5ka/codepathWeek7/blob/master/1_0hack.gif)
![](https://github.com/nke5ka/codepathWeek7/blob/master/1_1hack.gif)

## WordPress <= v4.2 - Unauthenticated Stored Cross-Site Scripting (CVE-2015-3440)
To get people to run the Javascript of the XSS exploit, the attacker posts a comment of form `<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px [64KB of words here]></a>`.  Though the comment is long, the admin might approve it if appears somewhat legitimate, or simply approves everything - the suspicious content can be easily hidden among all the text.  The exploit actually works because 64 KB of content is too much for the database to fuully store, and thus allows for the XSS attack to not be prevented.
![](https://github.com/nke5ka/codepathWeek7/blob/master/2_0hack.gif)
![](https://github.com/nke5ka/codepathWeek7/blob/master/2_1hack.gif)
![](https://github.com/nke5ka/codepathWeek7/blob/master/2_2hack.gif)

## WordPress v3.6.0-v4.7.2 - Authenticated Cross-Site Scripting (XSS) via Media File Metadata (2017-6814)
To do this exploit, convince an admin to upload a media file with xss javascript metadata - here is an example of a media file with a description and other metadata that I used: `https://www.securify.nl/advisory/SFY20160742/xss.mp3`.  Then upon viewing the attachment page, the Javascript is executed.
![](https://github.com/nke5ka/codepathWeek7/blob/master/3_0hack.gif)
![](https://github.com/nke5ka/codepathWeek7/blob/master/3_1hack.gif)
![](https://github.com/nke5ka/codepathWeek7/blob/master/3_2hack.gif)

## WordPress 4.2-4.7.2 - Press This CSRF DoS (CVE-2017-6819)
To perform this exploit, get a logged in admin to click on a link to a website with many lines containing `<img src='http://wpdistillery.vm/wp-admin/press-this.php?u=http%3A%2F%2Fhttps://127.0.0.1/foo.txt&url-scan-submit=Scan&a=g'>`.  Foo.txt contains many `<>` -  This setup causes the wordpress to try to scan for embedded content, leading to the server to be unresponsive for some time.