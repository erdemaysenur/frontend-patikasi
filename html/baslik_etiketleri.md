# Başlık Etiketleri 

# <head>

## title
- Sekme isminde yazar.
- Bu etiket arasına yazdıklarımız aynı zamanda sayfayı favorilere eklerken de karşımıza çıkar.
- Ayrıca arama motorları sayfamızın bu kısmına bakarak sitemizi listeler. Bu yüzden de oluşturduğumuz mükemmel web sayfalarının insanlara ulaşması için bu alanda yazdıklarımızın açıklayıcı, dikkat çekici ve 50-60 karakteri geçmeyecek şekilde ( Arama motorları genelde başlığın ilk 50-60 karakterini gösterir ) yazmamız gerekir.

## style

- Sayfanın nasıl görüneceği ile ilgili CSS belirteçleri burada yer alır.

## script

- Web sayfasında çalıştırılabilecek kodlar script etiketi arasında yazılır.
- HTML ve CSS birer işaretleme dili iken burada kullanılan Javascript bir programlama dilidir.
- Javascript sayesinde bir veri tabanıyla haberleşilebilir, sayfanın stili değiştirilebilir, animasyonlar çalıştırılabilinir.
- Tensorflow.js ile deep learning uygulamaları da bu etiket altında yazılır.
- Eğer script etiketini kullanırken herhangi bir özellik eklemezsek browser sırası geldiğinde doğrudan işlenir. Ve bu kısım işlenmeden sayfa yüklenmeye devam etmez. Bu noktada da *async* özelliğimiz devreye giriyor. Eğer sayfanın yüklenmeye devam ederken eşzamanlı olarak bu etiketlerle belirlediğimiz scriptlerin de yüklenmesini ve hazırlanmasını istiyorsak, yani bu kısmın asenkron çalışmasını istiyorsak etiketimize bu özelliği ekliyoruz. Herhangi bir değer girmemize gerek yok şu şekilde kullanabiliriz :

```
<script src="myJavascript.js" async></script>
```

- Eğer bu etiketin sayfa yüklendikten sonra yüklenip çalıştırılmasını istiyorsak o zaman *async* özelliğinin yanına ``defer`` özelliğini de eklememiz gerekiyor. **Ancak bu iki özellik de yalnızca sayfa harici kaynaktan yani bu HTML içinde yazmadığımız javascripti yüklerken kullanabileceğimiz özellikler. Buna da dikkat etmemiz gerekiyor.**
- Eğer bir kaynaktan(aynı domain dahil) bir şey yüklemek için belli bilgileri( Çerezlerimiz olabilir, HTTP basit giriş bilgileri olabilir) göndermemiz gerekiyorsa bu özelliğin değerini ``crossorigin = "use-credentials"`` olarak belirlemeliyiz. Eğer anonim şekilde erişmemiz gerekiyorsa yani herhangi bir bilgiye ihtiyaç yoksa ``crossorigin="anonymous"`` olarak kullanacağız.
- HTML sayfasına dış kaynaktan yüklenen bir scriptte güvenlik açığı var ise bundan bu scripti kullanan tüm sayfalar etkilenir. Bu noktada ``integrity`` özelliği devreye giriyor.
- integritynin mantığı şu şekilde; sayfaya eklenen hazır kodların bir imzası scripte bir özellik olarak eklenir. Bu imza kodun kendisinden olduşturulduğu için kodda yapılan değişiklikte artık imza tutmaz. Bu yüzden zararlı/zararsız herhangi bir değişiklikte kodlar sayfamıza yüklenmez.
```
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js" integrity="sha384-0mSbJDEHialfmuBBQP6A4Qrprq5OVfW37PRR3j5ELqxss1yVqOtnepnHVP9aJ7xS" crossorigin="anonymous"></script>
```
- Bir diğer script özelliği olan ``type`` ile scriptin tarayıcı tarafından nasıl yorumlanması gerektiğini belirtiriz. Örnek:

````
<script type="application/javascript">
document.getElementById("someTestDiv").innerHTML = "This code runs as js";
</script>
````

HTML sayfamızı oluştururken sayfa içerisindeki kod ne kadar uzun olursa okunması, yazılması ve incelenmesi o kadar zor olur. Bu yüzden kodları farklı sayfalara bölüp kullanmak hem daha kullanışlı hem de daha verimli olur. İşte bu amaçla farklı sayfalardaki scriptleri yükleyebilmek için de script etiketini kullanabiliriz. Bu amaçla script etiketinin *src* özelliğini kullanırız. Bu özellikle hem kendi dosya sistemimizde hem de internet üzerinde herhangi bir adreste bulunan kodları kendi sayfamıza ekleyebiliriz.

## link

- Farklı kaynaklardan farklı dosyaları sayfamızda kullanmak için bu etiketi kullanırız.
- Bu etikette de crossorigin özelliği mevcuttur.
- Bu etikette ilişki kurmak istediğimiz dış kaynağı href özelliği ile veriyoruz. Bu özelliğin açılımı Hypertext REFerence şeklindedir. Örnek olarak bir CSS sayfasını HTML dökümanımız ile ilişkilendirmek için şu kodu kullanabiliriz :

````
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous">
````

- Bu etiketin en önemli özelliklerinden birisi olan ``rel`` dış kaynaktan aldığımız dosyayı kendi HTML dokümanımızda ne şekilde ilişkilendirmek istediğimizi belirtmemize yarar. En çok kullanılan değerleri "stylesheet" ve "icon"dur. Stylesheet değerinde aldığımız dosyanın bir stil dosyası olduğunu belirtiriz ve HTML'imizi şekillendirmek için kullanır. Sekme yanına ikonlar eklemek için de ``rel = "icon"`` kullanıyoruz. Bulunduğumuz dizinde .ico uzantılı bir favicon.ico dosyamız varsa bu dosyayı sekmelerde ismin yanında ikon olarak göstermek üzere şöyle bir kod kullanabiliriz :

````
<link rel="icon" href="/favicon.ico" type="image/x-icon">
````

- link etiketi de type özelliği kullanır. Bu özellikle de ilişkilendirdiğimiz dosyanın tipini vermiş oluyoruz. Yaygın kullanılan değerleri stil dosyaları için ``type = "text/css"`` şeklinde, ikonlar için de ``type="image/x-icon"`` şeklindedir.

## meta

- HTML dokümanımızla ilgili verileri eklediğimiz etiket meta etiketidir.
- Burada eklediğimiz bilgiler sayfanın arama motorlarında, sosyal medya platformlarında vb. tanıtmak için kullanılır.
- Tarayıcının sayfada kullanılan alfabeyi doğru çözümleyebilmesi için ``charset`` özelliği kullanılır. Latin alfabesi için bu değer UTF-8'dir.
- Bir diğer önemli özelliğimiz ise ``http-equiv``'dir. Browserlar farklı sunuculara istek atarlarken belli bilgileri karşı tarafa gönderirler. İşte bu isteklerin arasında isteğin detaylarıyla ve yöntemiyle ilgili bilgilerin olduğu header'lar bulunur. Biz de dökümanımızda o dökümana ulaşan birisinin browser'inde header alanında bir bilgi tutmak istiyorsak bu meta etiketi özelliğini kullanabiliriz.

````
<meta http-equiv="Content-type" content="text/html" charset="UTF-8">
````

- Ayrıca ``refresh`` başlığını(header) bu meta yardımıyla belirleyerek sayfamızın belli sürede bir yenilenmesini veya belli bir süre sonra başka bir sayfaya yönlendirilmesini sağlayabiliriz.

````
<meta http-equiv="refresh" content="10;URL=kodluyoruz.html">
````
(Yukarıdaki kodda sayfa yüklendikten 10 saniye sonra URL ile verdiğimiz değer olan kodluyoruz.html'ye yönlendirilecek.)

- ``content`` olarak verdiğimiz değer meta olan verilen bilginin içeriğini tanımlamamızı sağlar.
- Son özelliğimiz de ``name`` özelliğimizdir. Bu da meta bilgi olarak vereceğimiz bilginin tanımlayıcısıdır diyebiliriz. Örnek olarak sayfamızda en çok geçen harfin ne olduğunu belirteceğimiz bir meta bilgisi yazmak isteyelim:

````
<meta name="enCokGecenHarf" content="a">
````

- Arama motorları bizi meta verilerinde verilen "keywords" lere göre sıralamaya alır :

````
<meta name="keywords" content="Kodluyoruz,programlama,web">
````

- Ayrıca arama motorlarında sayfa başlığının altındaki açıklamalarda da yine bu meta verilerine öncelik verilir :

````
<meta name="description" content="Kodluyoruzla web öğrenmeye hazır mısınız?">
````

- Bazı arama sonuçlarında yazar adı görürsünüz. Bu kısım da yine meta etiketinin marifetidir:

````
<meta name="author" content="Kodluyoruz">
````

- Meta etiketiyle söyleyeceğimiz son şey de ``viewport`` konusu. Akıllı telefonlarla birlikte geliştiriciler artık farklı cihazlara, farklı cihaz ekranlarında düzgün görünen kodlar yazmaya çalışıyor. Her ekranın genişliği boyutları farklı olduğu için tek bir ekran türüne göre tasarım ve kodlama yapmak da bu sorunu çözmüyor. Bu yüzden farklı cihazlarda da iyi görünen siteler yapmak için temel görünen alanı, bu alanın genişliğini vs tanımlamamız gerekiyor. İşte viewport burada yardımımıza koşuyor.

````
<meta name="viewport" content="width=device-width, initial-scale=1.0">
````

- Buraya kadar meta etiketini öğrendik peki sosyal medyalar ve arama motorları sitemizle ilgili bilgileri nasıl bu meta verilerden alıyor? Bu sorunun cevabı da yaygın kullanılan meta etiketleri kalıplarında bulunuyor. Örnek olarak github'da sağ tıklayıp sayfa kaynağını görüntüle dediğimizde karşımıza bir çok meta etiketi çıkıyor:

````
<meta property="og:url" content="https://github.com">
<meta property="og:site_name" content="GitHub">
<meta property="og:title" content="Build software better, together">
<meta property="og:description" content="GitHub is where people build software. More than 50 million people use GitHub to discover, fork, and contribute to over 100 million projects.">
<meta property="og:image" content="https://github.githubassets.com/images/modules/open_graph/github-logo.png">
<meta property="og:image:type" content="image/png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="1200">
<meta property="og:image" content="https://github.githubassets.com/images/modules/open_graph/github-mark.png">
<meta property="og:image:type" content="image/png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="620">
<meta property="og:image" content="https://github.githubassets.com/images/modules/open_graph/github-octocat.png">
<meta property="og:image:type" content="image/png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="620">

<meta property="twitter:site" content="github">
<meta property="twitter:creator" content="github">
<meta property="twitter:card" content="summary_large_image">
<meta property="twitter:title" content="GitHub">
<meta property="twitter:description" content="GitHub is where people build software. More than 50 million people use GitHub to discover, fork, and contribute to over 100 million projects.">
<meta property="twitter:image:src" content="https://github.githubassets.com/images/modules/open_graph/github-logo.png">
<meta property="twitter:image:width" content="1200">
<meta property="twitter:image:height" content="1200">
````

- İşte burada kullanılan meta taglar, facebook ve twitter paylaşımlarımızda bir url paylaşmak istediğimizde karşımıza çıkıyor. Sosyal medyada bir url paylaşmak istediğimizde url'yi kopyaladıktan sonra bir kart görürüz. Bu kartta bir başlık bir resim ve kısa bir açıklama bulunur. İşte o bilgiler bu meta verilerden alınır.


# </head>