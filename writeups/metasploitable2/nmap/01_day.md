# Metasploitable2

Bu dizin, Metasploitable2 hedefi üzerinde yapılan eJPT odaklı çalışmaları içerir.
Her gün ayrı dosya halinde belgelenmiştir.

Yerel ağda canlı sistemleri tespit etme amaçlı yapılan nmap taramasında -sn parametresi kullanılmış ve Metasploitable2 yerel ip adresi belirlenmiştir.
Metasplotable2 makinesinin üzerindeki açık TCP portlarını tespit edebilmek amacıyla nmap SYN taraması (-sS) kullanılmıştır
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
512/tcp  open  exec
513/tcp  open  login
514/tcp  open  shell
1099/tcp open  rmiregistry
1524/tcp open  ingreslock
2049/tcp open  nfs
2121/tcp open  ccproxy-ftp
3306/tcp open  mysql
5432/tcp open  postgresql
5900/tcp open  vnc
6000/tcp open  X11
6667/tcp open  ircrgre
8009/tcp open  ajp13
8180/tcp open  unknown
Tarama sonucunda yukarıda listelenen servislerin hedef sistem üzerinde erişilebilir durumda olduğu anlaşılmıştır.

Riskli olan portlar:

21/2121 – FTP, ccproxy-ftp 
Şifreleme kullanılmadığı için kimlik bilgileri ve dosya içerikleri ağ üzerinden okunabilir.

22/SSH 
Zayıf şifreleme veya yanlış yapılandırmaya karşı brute-force saldırılarına açıktır

23/Telnet 
Şifreleme olmadığı için iletişim düz metin olarak kolayca okunabilir

512/exec, 513/login, 514/shell 
Eski servisler olduğundan dolayı modern güvenlik protokollerini içermez ve izinsiz erişim sağlanabilir

139/44 5Netbios, SMB
İnternete açık olması durumunda dosya paylaşımı ve kimlik sızıntısına yol açabilir

5900/VNC
Grafik arayüzü sağlar, zayıf veya eksik doğrulama durumunda tam kullanıcı kontrolünü mümkün kılar

3306/Mysql, 5432/Postgre
Veritabanları servisleri dış erişime açık doğrudan veri sızıntısına yol açabilir 

80/HTTP
Web uygulamarı geniş saldırı yüzeyi olduğundan yapılandırma ve kimlik doğrulama hataları barındırabilir.
