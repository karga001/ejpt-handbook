DVWA’yı yerel makinem üzerine kurduktan ve güvenlik seviyesini Low olarak yapılandırdıktan sonra, ilk adım olarak brute-force saldırısını test etmeye karar verdim.

Bu aşamada ffuf aracını kullandım. Web login formu POST metodu ile çalıştığı için istekleri -X POST parametresi ile gönderdim ve -u parametresi ile hedef URL’yi belirledim.
POST isteğinin içeriğini -d parametresi ile tanımladım ve parola alanını fuzz edilecek şekilde yapılandırdım.

Brute-force işlemi sırasında kullanılacak parola listesini -w parametresi ile belirledim.
DVWA’nın kimlik doğrulama mekanizması nedeniyle geçerli bir oturum bilgisi gerekli olduğundan, PHPSESSID ve security level bilgilerini -H parametresi ile HTTP header olarak ekledim.

Yanlış giriş denemelerini ayıklamak için uygulamanın döndürdüğü hata mesajını -fr parametresi ile filtreledim.

<img width="1005" height="534" alt="resim" src="https://github.com/user-attachments/assets/cad5d896-41b0-4016-879f-ed26daf0c08b" />

Bu brute-force denemesi sonucunda admin kullanıcısı için parolayı 19026 olarak tespit ettim
