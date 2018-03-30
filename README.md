# codepathWeek7
For Network Security course at UVA.

## WordPress v2.5 to v4.6 - Authenticated Stored Cross-Site Scripting via Image Filename (CVE-2016-7168)
First step of this is social engineering - sending the admin a file that they would upload to the wordpress site.  The file is a trap, however!  The image is titled `dogsocute<img src=a onerror=alert("HACKED!!!")>.png` and when uploaded to the WP site will execute javascript!

![](https://github.com/nke5ka/codepathWeek7/blob/master/1_0hack.gif)
![](https://github.com/nke5ka/codepathWeek7/blob/master/1_1hack.gif)