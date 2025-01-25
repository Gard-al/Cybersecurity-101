# HTTP nedir? 

## HTTP nedir? (Köprü Metni Aktarım Protokolü)
 HTTP, 1989-1991 yılları arasında Tim Berners-Lee ve ekibi tarafından geliştirilen bir web sitesini görüntülediğinizde kullanılan şeydir. HTTP, HTML, Resimler, Videolar vb. gibi web sayfası verilerinin iletilmesi için web sunucularıyla iletişim kurmak için kullanılan kurallar kümesidir.

## HTTPS nedir? (Köprü Metni Aktarım Protokolü Güvenli)

 HTTPS, HTTP'nin güvenli sürümüdür. HTTPS verileri şifrelenir, bu nedenle yalnızca insanların aldığınız ve gönderdiğiniz verileri görmesini engellemekle kalmaz, aynı zamanda size doğru web sunucusuyla konuştuğunuza ve onu taklit eden bir şeyle konuşmadığınıza dair güvence verir.

#### Aşağıdaki soruları cevaplayın.

1- HTTP'nin açılımı nedir?

Cevap :  `HyperText Transfer Protocol`

2- HTTPS'deki S ne anlama geliyor?

Cevap : `Secure`

3- Sağdaki sahte web sayfasında bir sorun var, bulduktan sonra üzerine tıklayın. Meydan okuma bayrağı nedir? (Site içerisi etkileşim sorusu)

Cevap : `THM{INVALID_HTTP_CERT}`

# İstekler ve Yanıtlar 

 Bir web sitesine eriştiğimizde, tarayıcınızın HTML, Resimler gibi varlıklar için bir web sunucusuna istekte bulunması ve yanıtları indirmesi gerekir. Bundan önce, tarayıcıya özellikle bu kaynaklara nasıl ve nereden erişeceğini söylemeniz gerekir, URL'lerin yardımcı olacağı yer burasıdır.

## URL nedir? (Tekdüzen Kaynak Bulucu)
 İnterneti kullandıysanız, daha önce bir URL kullanmışsınızdır. Bir URL, ağırlıklı olarak internetteki bir kaynağa nasıl erişileceğine dair bir talimattır. Aşağıdaki resim, bir URL'nin tüm özellikleriyle nasıl göründüğünü gösterir (her istekte tüm özellikleri kullanmaz).
 

![scheme](https://github.com/user-attachments/assets/ee92ae9f-23dc-43ef-814d-38791b41498c)


Schema : Bu, HTTP, HTTPS, FTP (Dosya Aktarım Protokolü) gibi kaynağa erişmek için hangi protokolün kullanılacağı konusunda talimat verir.

User : Bazı hizmetler oturum açmak için kimlik doğrulaması gerektirir, oturum açmak için URL'ye bir kullanıcı adı ve şifre koyabilirsiniz.

Host/Domain : Erişmek istediğiniz sunucunun alan adı veya IP adresi.

Port : Bağlanacağınız Bağlantı Noktası, genellikle HTTP için 80 ve HTTPS için 443, ancak bu, 1 - 65535 arasındaki herhangi bir bağlantı noktasında barındırılabilir.

Path : Erişmeye çalıştığınız kaynağın dosya adı veya konumu.

Query String : İstenen yola gönderilebilecek ek bilgi parçaları. Örneğin, /blog? id=1, blog yoluna 1 kimliğine sahip blog makalesini almak istediğinizi söyler.

Fragment : Bu, istenen asıl sayfadaki bir konuma yapılan bir referanstır. Bu, genellikle uzun içeriğe sahip sayfalar için kullanılır ve sayfanın belirli bir bölümüne doğrudan bağlı olabilir, böylece kullanıcı sayfaya erişir erişmez görüntülenebilir.

## Talepte Bulunma 
 Bir web sunucusuna yalnızca bir satırla "GET / HTTP / 1.1" isteğinde bulunmak mümkündür.
 
![talep](https://github.com/user-attachments/assets/0f521945-c73b-4b75-afee-9db5a1b1c7b8)

 Ancak çok daha zengin bir web deneyimi için başka verileri de göndermeniz gerekir. Bu diğer veriler, başlıkların iletişim kurduğunuz web sunucusuna vermek için ekstra bilgiler içerdiği başlıklar adı verilen şekilde gönderilir, ancak Başlık görevinde buna daha fazla değineceğiz.

#### Örnek İstek:

 ```html
GET / HTTP/1.1

Host: tryhackme.com

User-Agent: Mozilla/5.0 Firefox/87.0

Referer: https://tryhackme.com/
```
Bu isteğin her satırının dökümünü almak için:

Satır 1: Bu istek GET yöntemini gönderiyor ( HTTP Yöntemleri görevinde bununla ilgili daha fazla bilgi ), / ile ana sayfayı isteyin ve web sunucusuna HTTP protokolü sürüm 1.1'i kullandığımızı söyleyin.

Satır 2: Web sunucusuna web sitesinin tryhackme.com istediğimizi söylüyoruz

Satır 3: Web sunucusuna Firefox sürüm 87 Tarayıcısını kullandığımızı söylüyoruz

Satır 4: Web sunucusuna, bizi bu sayfaya yönlendiren web sayfasının https://tryhackme.com olduğunu söylüyoruz

Satır 5: HTTP istekleri, web sunucusuna isteğin tamamlandığını bildirmek için her zaman boş bir satırla biter.

#### Örnek Yanıt:

 ```html
HTTP/1.1 200 OK

Server: nginx/1.15.8

Date: Fri, 09 Apr 2021 13:34:03 GMT

Content-Type: text/html

Content-Length: 98



<html>

<head>

    <title>TryHackMe</title>

</head>

<body>

    Welcome To TryHackMe.com

</body>

</html>
```
Yanıtın her satırının dökümünü almak için:

Satır 1: HTTP 1.1, sunucunun kullandığı HTTP protokolünün sürümüdür ve ardından bu durumda HTTP Durum Kodu "200 Ok" gelir ve bu bize isteğin başarıyla tamamlandığını söyler.

Satır 2: Bu bize web sunucusu yazılımını ve sürüm numarasını söyler.

Satır 3: Web sunucusunun geçerli tarihi, saati ve saat dilimi.

Satır 4: Content-Type başlığı, istemciye HTML, resimler, videolar, pdf, XML gibi ne tür bilgilerin gönderileceğini söyler.

Satır 5: Content-Length, istemciye yanıtın ne kadar sürdüğünü söyler, bu şekilde hiçbir verinin eksik olmadığını doğrulayabiliriz.

6. satır: HTTP yanıtı, HTTP yanıtının sonunu onaylamak için boş bir satır içerir.

7-14. satırlar: İstenen bilgiler, bu durumda ana sayfa.

#### Aşağıdaki soruları cevaplayın.

1- Yukarıdaki örnekte hangi HTTP protokolü kullanılıyor?

Cevap :  `HTTP/1.1`

2- Hangi yanıt üst bilgisi tarayıcıya ne kadar veri beklemesi gerektiğini söyler?

Cevap :  `Content-Length`

# HTTP Yöntemleri

 HTTP yöntemleri, istemcinin bir HTTP isteğinde bulunurken amaçladığı eylemi göstermesinin bir yoludur. Çok sayıda HTTP yöntemi vardır, ancak en yaygın olanları ele alacağız, ancak çoğunlukla GET ve POST yöntemiyle ilgileneceksiniz.

**GET Request**

Bu, bir web sunucusundan bilgi almak için kullanılır.

**POST Request**

Bu, web sunucusuna veri göndermek ve potansiyel olarak yeni kayıtlar oluşturmak için kullanılır

**PUT Request**

Bu, bilgileri güncellemek için bir web sunucusuna veri göndermek için kullanılır

**DELETE Request**

Bu, bir web sunucusundan bilgi/kayıt silmek için kullanılır.

#### Aşağıdaki soruları cevaplayın.

1- Yeni bir kullanıcı hesabı oluşturmak için hangi yöntem kullanılır?

Cevap :  `POST`

2- E-posta adresinizi güncellemek için hangi yöntem kullanılır?

Cevap :  `PUT`

3- Hesabınıza yüklediğiniz bir resmi kaldırmak için hangi yöntem kullanılır?

Cevap :  `DELETE`

4- Bir haber makalesini görüntülemek için hangi yöntem kullanılır?

Cevap :  `GET`
