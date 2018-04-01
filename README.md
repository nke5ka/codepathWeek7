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