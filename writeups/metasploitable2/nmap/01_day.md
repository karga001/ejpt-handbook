# Metasploitable2

Bu klasörde Metasploitable2 üzerinde yaptığım eJPT odaklı çalışmalara ait notlar var.  
Hepsi düzenli bir rapor şeklinde değil, daha çok süreçte aldığım notlar gibi tutuldu.

İlk olarak yerel ağda hangi makineler var görmek için basit bir Nmap taraması yaptım. Bu aşamada ayrıntı önemli değildi, sadece canlı sistemleri görmek yeterliydi. Bu sayede Metasploitable2 makinesinin yerel IP adresi ortaya çıktı.

Daha sonra hedef sistemde neler açık diye bakmak için SYN taraması kullandım. Burada amaç her servisi tek tek analiz etmekten çok, genel olarak sistemin ne kadar “açık” olduğunu görmekti. Çıkan sonuçlar aşağı yukarı şöyleydi:

21/tcp   ftp  
22/tcp   ssh  
25/tcp   smtp  
53/tcp   domain  
80/tcp   http  
111/tcp  rpcbind  
512/tcp  exec  
513/tcp  login  
514/tcp  shell  
1099/tcp rmiregistry  
1524/tcp ingreslock  
2121/tcp ccproxy-ftp  
3306/tcp mysql  
5432/tcp postgresql  
5900/tcp vnc  
6000/tcp X11  
6667/tcp irc  
8009/tcp ajp13  
8180/tcp unknown  

Listeye bakınca sistem üzerinde normalden fazla servis açık olduğu hemen fark ediliyor. Hepsi aynı derecede önemli değil ama bazıları özellikle göze çarpıyor.

FTP servisleri (21 ve 2121) şifreleme kullanılmadığı durumlarda her zaman soru işareti yaratıyor. Dosya erişimi ve kimlik bilgileri açısından kontrol edilmesi gereken servisler.

SSH tarafı (22) tek başına problem değil ama parola ayarları zayıfsa riskli hale gelebiliyor. Bu yüzden tamamen güvenli demek doğru olmaz.

512, 513 ve 514 numaralı portlarda çalışan servisler daha çok eski sistemlerde görülen şeyler. Güncel sistemlerde pek karşılaşılmıyor, bu da hedefin yapısı hakkında fikir veriyor.

VNC (5900) uzaktan erişim için kullanılıyor. Kimlik doğrulama tarafı zayıfsa sonuçları ağır olabilir.

Veritabanı servisleri (3306 ve 5432) dış erişime açık olduğunda doğrudan veriyi ilgilendiriyor. Bu yüzden ayrıca dikkat edilmesi gereken servisler arasında.

HTTP tarafı (80 ve 8180) zaten başlı başına geniş bir alan. Web uygulamaları genelde ayrı bir inceleme gerektiriyor, o yüzden burada sadece not düşmekle yetindim.

Bu aşamada hedef sistemi zorlamak veya derine inmek gibi bir amaç yoktu. Daha çok genel tabloyu görmek ve sonraki adımda nereye odaklanacağıma karar vermek için yapılan bir çalışmaydı.
