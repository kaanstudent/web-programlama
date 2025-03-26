# OTOBÜS BİLETİ REZERVASYON SİSTEMİ

**Hazırlayan:** Kaan

**Tarih:** 26 Mart 2025

---

# İÇİNDEKİLER

1. **GİRİŞ**
   - Projenin Amacı
   - Hedef Kitle
   - Sistem Gereksinimleri

2. **GENEL YAPI**
   - Dosya Organizasyonu
   - Kullanılan Teknolojiler
   - Mimari Yapı

3. **INDEX.PHP DOSYASI ANALİZİ**
   - Başlık ve Meta Etiketleri
   - CSS ve JavaScript Kütüphaneleri
   - Navigasyon Menüsü
   - Ana Sayfa Bölümü
   - Hakkımızda Bölümü
   - Footer Bölümü

4. **GİRİŞ SAYFASI ANALİZİ**
   - Oturum Yönetimi
   - Kullanıcı Girişi İşlemi
   - Form Yapısı ve Doğrulama
   - Güvenlik Önlemleri

5. **KULLANILAN TEKNOLOJİLER**
   - PHP
   - HTML5
   - CSS3 ve Bootstrap
   - JavaScript ve jQuery
   - Font Awesome

6. **KULLANICI DENEYİMİ**
   - Arayüz Tasarımı
   - Responsive Tasarım
   - Animasyonlar ve Etkileşimler

7. **GÜVENLİK ÖNLEMLERİ**
   - PHP Güvenliği
   - Kullanıcı Girişi Güvenliği
   - Veri Doğrulama
   - Şifre Güvenliği

8. **PERFORMANS OPTİMİZASYONU**
   - Sayfa Yükleme Hızı
   - Kaynak Optimizasyonu
   - Tarayıcı Önbelleği

---

# 1. GİRİŞ

## Projenin Amacı

Otobüs Bileti Rezervasyon Sistemi, yolcuların internet üzerinden kolayca otobüs bileti rezervasyonu yapabilmelerini sağlayan kapsamlı bir web uygulamasıdır. Bu sistem, geleneksel bilet satın alma sürecini dijitalleştirerek hem yolcular hem de otobüs işletmeleri için zaman ve kaynak tasarrufu sağlamayı amaçlamaktadır.

Proje, kullanıcıların evlerinin rahatlığında, 7/24 bilet rezervasyonu yapabilmelerini, mevcut koltukları görüntüleyebilmelerini, rota bilgilerini inceleyebilmelerini ve güvenli bir şekilde ödeme yapabilmelerini sağlayan bir platform sunmaktadır.

## Hedef Kitle

Sistemin hedef kitlesi şunları içermektedir:
- Otobüs ile seyahat eden yolcular
- Otobüs işletmeleri ve personeli
- Bilet satış acenteleri
- Sistem yöneticileri

## Sistem Gereksinimleri

Projenin çalışması için gerekli olan temel gereksinimler:
- PHP destekli bir web sunucusu (Apache, Nginx vb.)
- MySQL veritabanı
- Modern web tarayıcıları (Chrome, Firefox, Safari, Edge)
- Responsive tasarım desteği için mobil cihazlar

---

# 2. GENEL YAPI

## Dosya Organizasyonu

Proje, modüler bir yapıda organize edilmiştir ve aşağıdaki ana dosya ve klasörleri içermektedir:

- **index.php**: Ana giriş sayfası
- **constants.php**: Sistem genelinde kullanılan sabitler
- **conn.php**: Veritabanı bağlantı dosyası
- **pro/**: Kullanıcı ve yönetici panelleri
  - **signin.php**: Kullanıcı giriş sayfası
  - **adminsignin.php**: Yönetici giriş sayfası
  - **individual.php**: Kullanıcı paneli ana sayfası
  - **includes/**: Tekrar eden sayfa bileşenleri
    - **inc-header.php**: Sayfa başlığı
    - **inc-nav.php**: Navigasyon menüsü
- **css/**: Stil dosyaları
- **js/**: JavaScript dosyaları
- **library/**: Harici kütüphaneler
- **images/**: Sistem görselleri

## Kullanılan Teknolojiler

Proje, modern web geliştirme teknolojilerini kullanarak geliştirilmiştir:

- **Frontend**: HTML5, CSS3, JavaScript, jQuery, Bootstrap
- **Backend**: PHP
- **Veritabanı**: MySQL
- **Oturum Yönetimi**: PHP Session
- **Ek Kütüphaneler**: Font Awesome, Owl Carousel, Magnific Popup, SweetAlert2

## Mimari Yapı

Sistem, klasik bir web uygulaması mimarisine sahiptir:

1. **Sunum Katmanı**: HTML, CSS ve JavaScript ile oluşturulan kullanıcı arayüzü
2. **İş Mantığı Katmanı**: PHP ile yazılmış uygulama mantığı
3. **Veri Erişim Katmanı**: MySQL veritabanı ile etkileşim

---

# 3. INDEX.PHP DOSYASI ANALİZİ

## Başlık ve Meta Etiketleri

```php
<!DOCTYPE html>
<?php
include 'constants.php';
?>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=devidev-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title><?php echo @$title; ?></title>
    <!-- ... -->
</head>
```

Bu bölümde, sayfanın temel HTML yapısı ve meta etiketleri tanımlanmıştır. \`constants.php\` dosyası dahil edilerek, sistem genelinde kullanılan sabitler (örneğin site başlığı) erişilebilir hale getirilmiştir. Meta etiketleri, sayfanın karakter kodlamasını, görüntüleme alanını ve tarayıcı uyumluluğunu belirlemektedir.

## CSS ve JavaScript Kütüphaneleri

```html
<!-- [ FONT-AWESOME ICON ] -->
<link rel="stylesheet" type="text/css" href="library/font-awesome-4.3.0/css/font-awesome.min.css">

<!-- [ PLUGIN STYLESHEET ] -->
<link rel="shortcut icon" type="image/x-icon" href="images/icon.png">
<link rel="stylesheet" type="text/css" href="css/animate.css">
<link rel="stylesheet" type="text/css" href="css/owl.carousel.css">
<link rel="stylesheet" type="text/css" href="css/owl.theme.css">
<link rel="stylesheet" type="text/css" href="css/magnific-popup.css">

<!-- [ Boot STYLESHEET ] -->
<link rel="stylesheet" type="text/css" href="library/bootstrap/css/bootstrap-theme.min.css">
<link rel="stylesheet" type="text/css" href="library/bootstrap/css/bootstrap.css">

<!-- [ DEFAULT STYLESHEET ] -->
<link rel="stylesheet" type="text/css" href="css/style.css">
<link rel="stylesheet" type="text/css" href="css/responsive.css">
<link rel="stylesheet" type="text/css" href="css/color/themecolor.css">
```

Bu bölümde, sistemin görsel tasarımı ve işlevselliği için gerekli olan CSS ve JavaScript kütüphaneleri dahil edilmiştir. Kullanılan kütüphaneler şunlardır:

- **Font Awesome**: İkon kütüphanesi
- **Bootstrap**: Responsive tasarım çerçevesi
- **Owl Carousel**: Slider/carousel bileşeni
- **Magnific Popup**: Lightbox/popup bileşeni
- **Animate.css**: CSS animasyonları

Ayrıca, projeye özel stil dosyaları da dahil edilmiştir:
- style.css: Ana stil dosyası
- responsive.css: Responsive tasarım için stil dosyası
- themecolor.css: Tema renkleri için stil dosyası

## Navigasyon Menüsü

```html
<nav class="nim-menu navbar navbar-default navbar-fixed-top">
    <div class="container">
        <div class="navbar-header">
            <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
                <span class="sr-only">Gezinti menüsünü aç/kapat</span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
            </button>
            <a class="navbar-brand" href="index.php"><?php echo $title[0]; ?><span class="themecolor"><?php echo $title[1]; ?></span><?php for ($i = 2; $i < strlen($title); $i++) echo $title[$i]; ?></a>
        </div>

        <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav navbar-right">
                <li><a href="#home" class="page-scroll"><h3>Ana Sayfa</h3></a></li>
                <li><a href="#two" class="page-scroll"><h3>Hakkımızda</h3></a></li>
                <li><a href="pro/signin.php" class="page-scroll"><h3>Yolcu Paneli</h3></a></li>
                <li><a href="pro/adminsignin.php" class="page-scroll"><h3>Admin Panel</h3></a></li>
            </ul>
        </div>
    </div>
</nav>
```

Navigasyon menüsü, Bootstrap'in navbar bileşeni kullanılarak oluşturulmuştur. Menü, sayfanın üst kısmında sabit (fixed-top) olarak konumlandırılmıştır ve responsive tasarım için küçük ekranlarda hamburger menüsüne dönüşmektedir.

Menü öğeleri şunlardır:
- **Ana Sayfa**: Sayfanın üst kısmına yönlendirir
- **Hakkımızda**: Sayfanın "Hakkımızda" bölümüne yönlendirir
- **Yolcu Paneli**: Yolcuların giriş yapabileceği sayfaya yönlendirir
- **Admin Panel**: Yöneticilerin giriş yapabileceği sayfaya yönlendirir

Site başlığı, \`constants.php\` dosyasından alınan \`$title\` değişkeni kullanılarak dinamik olarak oluşturulmuştur. Başlığın ikinci karakteri tema rengiyle vurgulanmıştır.

## Ana Sayfa Bölümü

```html
<section class="main-heading" id="home">
    <div class="overlay">
        <div class="container">
            <div class="row">
                <div class="main-heading-content col-md-12 col-sm-12 text-center">
                    <h1 class="main-heading-title"><span class="main-element themecolor" data-elements="Online Bilet, Online Bilet Al, Online Bilet Satın Al"></span></h1>
                    <h1 class="main-heading-title"><span class="main-element themecolor" data-elements="Rezervasyon Sistemi, Rezervasyon Sistemi Kullan, Rezervasyon Sistemi Mükemmel"></span></h1>
                    <p class="main-heading-text">HOŞ GELDİNİZ,<br />OTOBÜSLER İÇİN E - BİLET SİSTEMİ</p>
                    <div class="btn-bar">
                        <a href="pro/signin.php" class="btn btn-custom theme_background_color">Şimdi Rezervasyon Yapın</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
```

Ana sayfa bölümü, kullanıcıları karşılayan ve sistemin ana amacını vurgulayan bir hero section içermektedir. Bu bölümde, animasyonlu metin efektleri için \`main-element\` sınıfı kullanılmıştır. JavaScript ile bu metinler sırayla değiştirilerek dinamik bir görünüm elde edilmektedir.

Bölüm, kullanıcıları "Şimdi Rezervasyon Yapın" butonu ile yolcu giriş sayfasına yönlendirmektedir.

Ayrıca, ikinci bir ana sayfa bölümü de bulunmaktadır:

```html
<section class="main-heading" id="home">
    <div class="overlay">
        <div class="container">
            <div class="row">
                <div class="main-heading-content col-md-12 col-sm-12 text-center">
                    <h1 class="main-heading-title">MZR Otobüs Seyahati ve Bilet Satış Platformu A.Ş.</h1>
                    <p class="main-heading-text">MZR Otobüs Şirketi 112 yıllık bir geçmişe sahiptir ve tek taraflı tasarlanmış 1067mm genişliğinde bir yol sistemi işletmektedir. Yol ağının yalnızca 30 km'lik kısmı çift şeritlidir ve bu bölüm Lagos bölgesindedir. 
                    <br />MZR otobüs dar yol ağı yaklaşık 3.500 km uzunluğundadır ve şu anda ABC ile BCA - Port Harcourt hattı arasında bir dar yol hattı ile Ikakpe – Ajaokuta – Warri arasında 275 km uzunluğunda bir standart yol hattı eklenerek genişletilmektedir.</p>
                    <div class="btn-bar">
                        <a href="system/" class="btn btn-custom theme_background_color">Başlayın</a>
                        <a href="/pro/signin.php" class="btn btn-custom-outline">Şimdi Başla</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
```

Bu bölüm, MZR Otobüs Şirketi hakkında bilgi vermekte ve kullanıcıları sistemi kullanmaya teşvik etmektedir. İki farklı buton ile kullanıcılar sisteme yönlendirilmektedir.

## Hakkımızda Bölümü

```html
<section class="aboutus white-background black" id="two">
    <div class="container">
        <div class="row">
            <div class="col-md-12 text-center black">
                <h3 class="title">HAKKI<span class="themecolor">MIZDA</span></h3>
            </div>
        </div>
        <div class="gap"></div>
        <div class="row about-box">
            <div class="col-sm-4 text-center">
                <div class="margin-bottom">
                    <i class="fa fa-newspaper-o"></i>
                    <h4>Evinizin Rahatlığında Otobüs Bileti Alın</h4>
                    <p class="black">Güçlü biletleme platformunu kullanarak her yerden otobüs bileti rezervasyonu yapın Yolculara keyifli bir biletleme deneyimi sunmak için özel olarak inşa edilmiştir.</p>
                </div>
            </div>
            <div class="col-sm-4 about-line text-center">
                <div class="margin-bottom">
                    <i class="fa fa-diamond"></i>
                    <h4>Otobüs ve Biletleme ile ilgili bilgiler parmaklarınızın ucunda</h4>
                    <p class="black">Mevcut koltukları, rota bilgilerini, ücret bilgilerini gerçek zamanlı olarak kontrol edin Esheba Platformu ile temel.</p>
                </div>
            </div>
            <div class="col-sm-4 text-center">
                <div class="margin-bottom">
                    <i class="fa fa-dollar"></i>
                    <h4>Güvenli Ödeme & İade, Değişim Hakları</h4>
                    <p class="black">Online ödeme işlemi güvenli bir şekilde yapılır. Lütfen biletinizi dikkatlice kontrol edin, çünkü tüm biletler için iade veya değişim yapılmamaktadır.</p>
                </div>
            </div>
        </div>
    </div>
</section>
```

Hakkımızda bölümü, sistemin üç ana özelliğini vurgulamaktadır:

1. **Kolay Erişim**: Kullanıcılar evlerinin rahatlığında bilet alabilirler
2. **Bilgi Erişimi**: Kullanıcılar koltuk, rota ve ücret bilgilerine kolayca erişebilirler
3. **Güvenli Ödeme**: Kullanıcılar güvenli bir şekilde ödeme yapabilirler

Her özellik, ilgili bir Font Awesome ikonu ile görselleştirilmiştir ve kısa bir açıklama ile desteklenmiştir.

## Footer Bölümü

```html
<footer class="site-footer section-spacing text-center " id="eight">
    <div class="container">
        <div class="row">
            <div class="col-md-4">
                <p class="footer-links"><a href="#">Kullanım Koşulları</a> <a href="#">Gizlilik Politikası</a></p>
            </div>
            <div class="col-md-4">
                <!--social-->
                <!-- 
                <ul class="social">
                  <li><a href="https://twitter.com/" target="_blank"><i class="fa fa-twitter "></i></a></li>
                  <li><a href="https://www.facebook.com/" target="_blank"><i class="fa fa-facebook"></i></a></li>
                  <li><a href="https://www.youtube.com/" target="_blank"><i class="fa fa-youtube-play"></i></a></li>
                </ul> -->
                <!--social end-->
            </div>
        </div>
    </div>
</footer>
```

Footer bölümü, sayfanın alt kısmında yer alan basit bir yapıdır. Kullanım Koşulları ve Gizlilik Politikası bağlantıları içermektedir. Sosyal medya bağlantıları için bir bölüm bulunmakla birlikte, bu bölüm şu anda yorum satırına alınmıştır.

---

# 4. GİRİŞ SAYFASI ANALİZİ

## Oturum Yönetimi

```php
<?php
session_start();
require_once '../conn.php';
$class = "signin";
?>
```

Giriş sayfası, PHP'nin oturum yönetimi mekanizmasını kullanmaktadır. \`session_start()\` fonksiyonu ile oturum başlatılmakta ve kullanıcı bilgileri oturum değişkenlerinde saklanmaktadır. Ayrıca, veritabanı bağlantısı için \`conn.php\` dosyası dahil edilmektedir.

\`$class\` değişkeni, sayfanın CSS sınıfını belirlemek için kullanılmaktadır. Bu değişken, sayfa şablonunda (inc-header.php) kullanılarak, sayfaya özel stil uygulanmasını sağlamaktadır.

## Kullanıcı Girişi İşlemi

```php
<?php
$cur_page = 'signup';
include 'includes/inc-header.php';
include 'includes/inc-nav.php';
if (isset($_POST['email'])) {
    $email = $_POST['email'];
    $password = $_POST['password'];
    if (!isset($email, $password)) {
?>
<script>
alert("Formu doğru şekilde doldurduğunuzdan emin olun.");
</script>
<?php
    } else {

        //Check for login
        $password = md5($password);
        $check = $conn->prepare("SELECT * FROM passenger WHERE email = ? AND password = ?");
        $check->bind_param("ss", $email, $password);
        if (!$check->execute()) die("Form Hata İle Dolduruldu");
        $res = $check->get_result();
        $no_rows = $res->num_rows;
        if ($no_rows ==  1) {
            $row = $res->fetch_assoc();
            $id = $row['id'];
            $status = $row['status'];
            if ($status != 1) {
        ?>
<script>
alert("Hesap Devre Dışı Bırakıldı!\nSistem Yöneticisi ile İletişime Geçin!");
window.location = "signin.php";
</script>
<?php
                exit;
            }
            session_regenerate_id(true);
            $_SESSION['user_id'] = $id;
            $_SESSION['email'] = $email;

            ?>
<script>
alert("Giriş Başarılı!");
window.location = "individual.php";
</script>
<?php
            exit;
        } else { ?>
<script>
alert("Bu bilgilere sahip bir hesap bulunamadı veya bilgiler hatalı!");
</script>
<?php
        }
    }
}
?>
```

Kullanıcı girişi işlemi, form gönderildiğinde (POST metodu ile) gerçekleştirilmektedir. İşlem adımları şu şekildedir:

1. Form verilerinin alınması ve doğrulanması
2. Şifrenin MD5 algoritması ile şifrelenmesi
3. Veritabanında kullanıcı bilgilerinin kontrol edilmesi
4. Kullanıcı bulunursa, hesap durumunun kontrol edilmesi
5. Hesap aktif ise, oturum değişkenlerinin ayarlanması ve kullanıcının yönlendirilmesi
6. Kullanıcı bulunamazsa veya hesap devre dışı ise, hata mesajının gösterilmesi

Güvenlik açısından, hazırlıklı ifadeler (prepared statements) kullanılarak SQL enjeksiyonu saldırılarına karşı önlem alınmıştır. Ayrıca, \`session_regenerate_id(true)\` fonksiyonu ile oturum kimliği yenilenerek, oturum hırsızlığı saldırılarına karşı önlem alınmıştır.

## Form Yapısı ve Doğrulama

```html
<div class="signup-page">
    <div class="form">
        <h2>Müşteri Paneli</h2>
        <br>
        <form class="login-form" method="post" role="form" id="signup-form" autocomplete="off">
            <!-- json response will be here -->
            <div id="errorDiv"></div>
            <!-- json response will be here -->

            <div class="col-md-12">
                <div class="form-group">
                    <label>E-posta Adresi</label>
                    <input type="email" required name="email">
                </div>
            </div>

            <div class="col-md-12">
                <div class="form-group">
                    <label>Şifre</label>
                    <input type="password" name="password" id="password">
                    <span class="help-block" id="error"></span>
                </div>
            </div>

            <div class="col-md-12">
                <div class="form-group">
                    <button type="submit" id="btn-signup">
                        Giriş Yap
                    </button>
                </div>
            </div>
            <p class="message">
                <a href="#">.</a><br>
            </p>
        </form>
    </div>
</div>
```

Giriş formu, kullanıcıdan e-posta adresi ve şifre bilgilerini istemektedir. Form, POST metodu ile aynı sayfaya gönderilmektedir. Form doğrulaması için HTML5'in \`required\` özelliği ve \`type="email"\` gibi özellikleri kullanılmaktadır.

Form, Bootstrap'in grid sistemi ve form bileşenleri kullanılarak oluşturulmuştur. Her form alanı, bir \`form-group\` içinde yer almakta ve bir etiket (label) ile açıklanmaktadır.

Hata mesajları için \`errorDiv\` ve \`error\` id'li elementler bulunmaktadır. Bu elementler, JavaScript ile form doğrulaması sırasında veya sunucu tarafından dönen hata mesajlarını göstermek için kullanılabilir.

## Güvenlik Önlemleri

Giriş sayfasında alınan güvenlik önlemleri şunlardır:

1. **SQL Enjeksiyonu Koruması**: Hazırlıklı ifadeler (prepared statements) kullanılarak, kullanıcı girdilerinin SQL sorgularına doğrudan eklenmesi engellenmiştir.

```php
$check = $conn->prepare("SELECT * FROM passenger WHERE email = ? AND password = ?");
$check->bind_param("ss", $email, $password);
```

2. **Şifre Şifreleme**: Kullanıcı şifreleri, MD5 algoritması ile şifrelenerek veritabanında saklanmaktadır. Ancak, MD5 algoritması günümüzde güvenli kabul edilmemektedir ve daha güçlü şifreleme algoritmaları (bcrypt, Argon2 vb.) kullanılması önerilmektedir.

```php
$password = md5($password);
```

3. **Oturum Güvenliği**: Kullanıcı girişi başarılı olduğunda, oturum kimliği yenilenerek oturum hırsızlığı saldırılarına karşı önlem alınmıştır.

```php
session_regenerate_id(true);
```

4. **Hesap Durumu Kontrolü**: Kullanıcı hesabının aktif olup olmadığı kontrol edilerek, devre dışı bırakılmış hesapların girişi engellenmektedir.

```php
if ($status != 1) {
    // Hesap devre dışı
}
```

I'll create a complete version of the pdf-content-updated.js file that contains the entire PDF content, including both the index.php and signin.php analysis.
`</Thinking>`

Haklısınız, tüm PDF içeriğini pdf-content-updated.js dosyasının içine yerleştireceğim. İşte tam ve eksiksiz içerik:

```javascript project="Bus Ticket Booking System PDF" file="pdf-content-updated.js"
...
```

SweetAlert2 kütüphanesi, standart JavaScript alert kutularını daha modern ve kullanıcı dostu alert kutuları ile değiştirmek için kullanılabilir. Ancak, mevcut kodda bu kütüphane doğrudan kullanılmamaktadır ve standart JavaScript alert fonksiyonu kullanılmaktadır.

---

# 5. KULLANILAN TEKNOLOJİLER

## PHP

PHP, sistemin sunucu tarafı işlemlerini gerçekleştirmek için kullanılmıştır. PHP ile gerçekleştirilen işlemler şunlardır:

- Oturum yönetimi
- Veritabanı işlemleri
- Form işleme
- Kullanıcı doğrulama
- Dinamik içerik oluşturma


```php
<?php
session_start();
require_once '../conn.php';
$class = "signin";
?>
```

## HTML5

Sistem, modern HTML5 standartlarına uygun olarak geliştirilmiştir. Semantik HTML etiketleri (section, nav, footer vb.) kullanılarak, sayfanın yapısı ve anlamı güçlendirilmiştir. Ayrıca, HTML5'in form doğrulama özellikleri (`required`, `type="email"` vb.) kullanılarak, kullanıcı girdilerinin doğrulanması sağlanmıştır.

```html
<input type="email" required name="email">
```

## CSS3 ve Bootstrap

Sistemin görsel tasarımı, CSS3 ve Bootstrap çerçevesi kullanılarak oluşturulmuştur. Bootstrap, responsive tasarım için grid sistemi ve hazır bileşenler sağlarken, özel CSS dosyaları ile sistemin kendine özgü görünümü elde edilmiştir.

```html
<link rel="stylesheet" type="text/css" href="library/bootstrap/css/bootstrap-theme.min.css">
<link rel="stylesheet" type="text/css" href="library/bootstrap/css/bootstrap.css">
<link rel="stylesheet" type="text/css" href="css/style.css">
<link rel="stylesheet" type="text/css" href="css/responsive.css">
<link rel="stylesheet" type="text/css" href="css/color/themecolor.css">
```

## JavaScript ve jQuery

Sistemin interaktif özellikleri, JavaScript ve jQuery kütüphanesi kullanılarak geliştirilmiştir. JavaScript ile gerçekleştirilen işlemler şunlardır:

- Form doğrulama
- Kullanıcı bildirimleri (alert)
- Sayfa yönlendirme
- Animasyonlar ve efektler


```html
<script src="assets/js/jquery-1.12.4-jquery.min.js"></script>
<script src="assets/js/sweetalert2.js"></script>
```

SweetAlert2 kütüphanesi, daha modern ve kullanıcı dostu bildirim kutuları oluşturmak için kullanılabilir, ancak mevcut kodda standart JavaScript alert fonksiyonu tercih edilmiştir.

## Font Awesome

Sistemde kullanılan ikonlar, Font Awesome kütüphanesinden sağlanmıştır. Bu kütüphane, vektör tabanlı ikonlar sunarak, farklı ekran boyutlarında kaliteli görüntü elde edilmesini sağlamaktadır.

```html
<link rel="stylesheet" type="text/css" href="library/font-awesome-4.3.0/css/font-awesome.min.css">
...
<i class="fa fa-newspaper-o"></i>
<i class="fa fa-diamond"></i>
<i class="fa fa-dollar"></i>
```

---

# 6. KULLANICI DENEYİMİ

## Arayüz Tasarımı

Sistemin arayüz tasarımı, kullanıcı dostu bir deneyim sunmak üzere tasarlanmıştır. Ana sayfa, kullanıcıları karşılayan çarpıcı bir hero section ile başlamakta ve sistemin ana özelliklerini vurgulayan bölümlerle devam etmektedir.

Giriş sayfası ise, temiz ve odaklanmış bir tasarıma sahiptir. Kullanıcıdan sadece gerekli bilgiler (e-posta ve şifre) istenmekte ve form alanları açık bir şekilde etiketlenmektedir.

Tasarım, temiz ve modern bir görünüme sahiptir. Beyaz arka plan üzerine siyah metin kullanılarak okunabilirlik artırılmış, tema rengi ile vurgular yapılarak görsel hiyerarşi oluşturulmuştur.

## Responsive Tasarım

Sistem, Bootstrap çerçevesi kullanılarak responsive bir tasarıma sahip olacak şekilde geliştirilmiştir. Bu sayede, farklı ekran boyutlarına (masaüstü, tablet, mobil) uyum sağlayabilmektedir.

```html
<meta name="viewport" content="width=devidev-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
...
<div class="col-md-12 col-sm-12 text-center">
...
<div class="col-sm-4 text-center">
```

Navigasyon menüsü, küçük ekranlarda hamburger menüsüne dönüşmektedir:

```html
<button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
    <span class="sr-only">Gezinti menüsünü aç/kapat</span>
    <span class="icon-bar"></span>
    <span class="icon-bar"></span>
    <span class="icon-bar"></span>
</button>
```

## Animasyonlar ve Etkileşimler

Sistem, kullanıcı deneyimini zenginleştirmek için çeşitli animasyonlar ve etkileşimler içermektedir. Ana sayfadaki animasyonlu metin efektleri, `typed.js` kütüphanesi kullanılarak oluşturulmuştur:

```html
<h1 class="main-heading-title"><span class="main-element themecolor" data-elements="Online Bilet, Online Bilet Al, Online Bilet Satın Al"></span></h1>
```

Sayfa kaydırma işlemi, `SmoothScroll.js` kütüphanesi ile yumuşak bir şekilde gerçekleştirilmektedir:

```html
<script type="text/javascript" src="js/SmoothScroll.js"></script>
```

Kullanıcı bildirimleri, JavaScript alert fonksiyonu ile gösterilmektedir:

```javascript
alert("Giriş Başarılı!");
window.location = "individual.php";
```

---

# 7. GÜVENLİK ÖNLEMLERİ

## PHP Güvenliği

Sistemde PHP güvenliği için alınan önlemler şunlardır:

- Hazırlıklı ifadeler (prepared statements) kullanılarak SQL enjeksiyonu saldırılarına karşı koruma
- Oturum kimliğinin yenilenmesi ile oturum hırsızlığı saldırılarına karşı koruma
- Kullanıcı girdilerinin doğrulanması


Ancak, bazı güvenlik açıkları da bulunmaktadır:

```php
<title><?php echo @$title; ?></title>
```

Burada, `@` operatörü ile hata bastırılmaktadır. Bu, güvenlik açısından iyi bir uygulama değildir. Hataların bastırılması yerine, değişkenin varlığı kontrol edilmelidir:

```php
<title><?php echo isset($title) ? $title : 'Otobüs Bileti Rezervasyon Sistemi'; ?></title>
```

## Kullanıcı Girişi Güvenliği

Kullanıcı girişi güvenliği için alınan önlemler şunlardır:

- Hazırlıklı ifadeler (prepared statements) kullanılarak SQL enjeksiyonu saldırılarına karşı koruma
- Şifrelerin MD5 algoritması ile şifrelenmesi
- Oturum kimliğinin yenilenmesi ile oturum hırsızlığı saldırılarına karşı koruma
- Hesap durumunun kontrol edilmesi


```php
$password = md5($password);
$check = $conn->prepare("SELECT * FROM passenger WHERE email = ? AND password = ?");
$check->bind_param("ss", $email, $password);
...
session_regenerate_id(true);
```

Ancak, MD5 algoritması günümüzde güvenli kabul edilmemektedir ve daha güçlü şifreleme algoritmaları (bcrypt, Argon2 vb.) kullanılması önerilmektedir.

## Veri Doğrulama

Kullanıcı girdilerinin doğrulanması için alınan önlemler şunlardır:

- HTML5 form doğrulama özellikleri (`required`, `type="email"` vb.)
- Sunucu tarafında PHP ile doğrulama


```html
<input type="email" required name="email">
```

```php
if (!isset($email, $password)) {
    // Hata mesajı
}
```

## Şifre Güvenliği

Şifre güvenliği için alınan önlemler şunlardır:

- Şifrelerin MD5 algoritması ile şifrelenmesi
- Şifre alanının `type="password"` olarak tanımlanması


```php
$password = md5($password);
```

```html
<input type="password" name="password" id="password">
```

Ancak, MD5 algoritması günümüzde güvenli kabul edilmemektedir ve daha güçlü şifreleme algoritmaları (bcrypt, Argon2 vb.) kullanılması önerilmektedir. Ayrıca, şifre politikası (minimum uzunluk, karmaşıklık vb.) uygulanması da önerilmektedir.

---

# 8. PERFORMANS OPTİMİZASYONU

## Sayfa Yükleme Hızı

Sistemin performansı, kullanıcı deneyimini doğrudan etkilemektedir. Sayfa yükleme hızını artırmak için şu optimizasyonlar yapılabilir:

- CSS ve JavaScript dosyalarının minify edilmesi
- Görsel dosyaların optimize edilmesi
- HTTP isteklerinin azaltılması
- Önbellek kullanımı
- CDN (Content Delivery Network) kullanımı


## Kaynak Optimizasyonu

Sistemde, çok sayıda harici CSS ve JavaScript dosyası dahil edilmiştir. Bu dosyaların birleştirilmesi ve sıkıştırılması, sayfa yükleme hızını artıracaktır.

```html
<link rel="stylesheet" type="text/css" href="css/animate.css">
<link rel="stylesheet" type="text/css" href="css/owl.carousel.css">
<link rel="stylesheet" type="text/css" href="css/owl.theme.css">
<link rel="stylesheet" type="text/css" href="css/magnific-popup.css">
```

Bu dosyalar, tek bir CSS dosyasında birleştirilebilir:

```html
<link rel="stylesheet" type="text/css" href="css/plugins.min.css">
```

Benzer şekilde, JavaScript dosyaları da birleştirilebilir:

```html
<script src="js/plugins.min.js"></script>
```

## Tarayıcı Önbelleği

Statik dosyaların (CSS, JavaScript, görsel vb.) tarayıcı önbelleğinde saklanması, tekrarlanan sayfa ziyaretlerinde yükleme hızını artıracaktır. Bu, HTTP başlıkları ile yapılandırılabilir:

```plaintext
Cache-Control: max-age=31536000
Expires: [gelecek tarih]
```
