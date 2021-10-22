# CSS Seçiciler ile Çalışmak, İstediğimiz HTML Etiket Yapısına Özelliklik Ekleyebilmek (Selectors)

## Genel Seçici

Bu seçiciyle bütün etiketlere stil uygulanır.

````
*{
  margin:0;
  padding:0;
}
div *{
  color:orange;
}
````

İkinci seçici tüm div elementlerine stili uygular. 

## Element Seçici

````
div{
  background-color: orange;
}
````

## Class Selectors
````
.turuncu{
  background-color: #FFA500;
}
p.mavi{
  color:blue;
}
 <p class="turuncu">Arka plan rengim turuncu</p>
 <div class="turuncu">Arka plan rengim turuncu</div>
 ````
 
İlk selector class ataması turuncu olan durumlarda herhangi bir etikette kullanılabilir. İkinci selector ise p etiketli classı mavi olarak atanan durumlarda uygulanır.

## Id Selectors
````
#mavi{
  background-color: #0000FF;
}
#lila{
  color: #c8a2c8;
}
 <p id="mavi">Arka plan rengim turuncu</p>
 <div id="lila">yazı rengim lila</div>
 ````
 Bu seçiciler ile id atadığımız elementlere CSS uygulayabiliriz. Id' ler tek bir elemente ait olmalıdırlar. Id özelliğine erişmek id' nin başına # ekliyoruz.
 
## Attribute Selectors

Bu seçiciler ile özelliğini belirttiğimiz elementlere CSS uygulayabiliriz. Özelliğin içi boş olsa da element bundan etkilenecektir. Özelliklere erişmek için yapmamız gereken tek şey köşeli parantezler içinde özelliğin ismini [attribute] şeklinde yazıyoruz.

````
[name]{
  color: orange;
}
<button name="">gönder</button>
<ul>
  ﻿<li name="html">HTML</li><li name="css">CSS</li>
</ul>
````
Bu şekilde name attribute alan tüm elementler etkilenir.

````
.btn[disabled] {
  color: orchid;
}
<button class="btn" disabled="disabled">Submit</button>
````
 
 Burada sınıfı .btn ve niteliği(attribute) [disabled] olan butona CSS uyguladık.
 
````
div[title="deneme"] {
  background-color: orange;
}
<div title="Deneme">Lorem, ipsum dolor.</div>
<div title="deneme">Lorem, ipsum dolor.</div>
<div name="denemefalan">Lorem, ipsum.</div>
````
 
 Burada tam eşleşen özelliğe CSS uyguladık. Büyük-küçük harf duyarlılığı vardır.
 
 ````
 div[title~="isim"] {
  color: orange;
}
<div title="isim">Lorem, ipsum dolor.</div>
<div title="isimler">Lorem, ipsum dolor.</div>
<div title="isim ve şehirler">Lorem, ipsum dolor.</div>
````

**Burada ~= ifadesi ile title özelliği "isim" içeren divlere eriştik.**
 
 ````
 a[href ^= "https"] {
  color: palegreen;
}
<a href="https://www.google.com/">google</a>
<a href="https://github.com/">github</a>
<a href="http://github.com/">github</a>
````
**Burada ^= ifadesi ile href özelliği "https" ile başlayan a etiketlerine eriştik.**

````
a[href *= "http"] {
  color: palegreen;
}
<a href="https://www.google.com/">google</a>
<a href="https://github.com/">github</a>
<a href="http://github.com/">github</a>
````
**Burada** *= **ifadesi ile href özelliği "http" içeren a etiketlerine eriştik.**
````
div[class$="test"] {
  background: yellow;
}
<div class="bir_test">Lorem, ipsum dolor.</div>
<div class="iki-test">Lorem, ipsum dolor.</div>
<div class="uc test">Lorem, ipsum dolor.</div>
<div class="dorttest">Lorem, ipsum dolor.</div>
````
**Burada $= ifadesi ile class özelliği sonunda "test" içeren divlere eriştik.**

````
div[class$="test"] {
  background: yellow;
}
<div class="bir_test">Lorem, ipsum dolor.</div>
<div class="iki-test">Lorem, ipsum dolor.</div>
<div class="uc test">Lorem, ipsum dolor.</div>
<div class="dorttest">Lorem, ipsum dolor.</div>
````
**Burada $= ifadesi ile class özelliği sonunda "test" içeren divlere eriştik.**

````
a[href*="https"][href$="com"] {
        color: orange;
}
<a href="https://www.google.com/"></a>
<a href="https://reactjs.org/"></a>
<a href="https://css-tricks.com/"></a>
````
**Burada https ile başlayan ve sonunda com olan a etiketlerine eriştik.**

## Child Selectors

Etketleri birbirleriyle olan hiyerarşik durumuna göre seçerek css özelliklerini belirlemek için bu seçici kullanılır.

````
p > span{
  color:orange;
}
p > span >b{
  color:blue;
}
div > ul >li#first{
  color:red;
}
<p>
  <span>child element</span>
</p>
````
Parent etiketi yani bir üst kapsayıcısı p olan span etiketine ulaştık.
````
<p>
  <span>Burası turuncu renkte <b>mavi renkte yazılacak</b></span>
</p>
<p>
  <span>Burası turuncu renkte <b>mavi renkte yazılacak</b></span>
</p>
<div>
  ﻿<ul>
    ﻿<li id="first">bir</li>
    <li>iki</li>
  ﻿</ul>
</div>
````
 
 ## Descentad Selectors
 
 Bir kapsayıcı yani parent element altındaki tüm etiketlere ulaşmak için kullanılır. Her ulaşılacak etiket arasına boşluk konulur.
 
 ````
 div p{
  background-color:blue;
}
````
Burada div içinde olan tüm p etiketlerine ulaşırız.
````
<div>
  <p>Bu p etiketi arka planı mavi renk</p>
  <ul>
    <li>
      <p>Bu p etiketi arka planı mavi renk</p>
    </li>
  </ul>
  <p>Bu p etiketi arka planı mavi renk</p>
</div>
````

## Genel Kardeş Seçiciler (General Sibling Selectors)

Aynı parent etikete sahip olan ve birbiri ardına gelen etiketleri seçmek için kullanılır.

````
ul ~ p{
  color:orange;
}
<div>
  <p>Lorem, ipsum.</p>
  <ul>
    <li>
      <p>Lorem, ipsum dolor.</p>
    </li>
  </ul>
  <h3>Lorem, ipsum dolor.</h3>
  <p>Bu p etiketi turuncu renkte</p>
</div>
````
Burada dikkat edilmesi gereken iki nokta var. Birincisi <p> etiketi <ul> etiketinden sonra gelmeli (arada başka etiketler olabilir) ve ikisi de aynı düzeyde yani aynı parent etiketine sahip olmalılar.

## Bitişik Kardeş Seçiciler (Adjacent Sibling Selector)

Genel kardeş seçiciden tek farkı belirtilen etiketler bitişik arka arkaya gelmeliler. + işareti ile gösterilir.
 
 ````
 ul + p{
  color:green;
}
<div>
  <p>Lorem, ipsum.</p>
  <ul>
    <li>
      <p>Lorem, ipsum.</p>
    </li>
  </ul>
  <p>Bu p etiketinin yazı rengi yeşil</p>
</div>
````

## Pseudo Classes

Sahte sınıflar kullanarak HTML etiketlerine CSS uygulayabiliriz. Kullanımları ``selector:pseudo class{}``şeklindedir.

``:link``

````
a#google:link {
  color: red;
}
<a id="google" href="https://www.google.com/">Google</a>
````

``:hover``
````
a.test:hover {
  color: red;
}
<a class="test" href="https://www.github.com/">Github</a>
````
Burada a etiketinde test sınıflı elementin üzerine gelindiğinde rengi kırmızı olur.
 
 ``:active``
 ````
 a:active {
  position: relative;
  top: 5px;
}
<a href="#">Submit</a>
````
Mouse ile tıklandığında CSS uygulanır. Tıklama kaldırıldığında etki kaybolur.

``:first-child``
İlk child etikete CSS uygulanır.
````
ul > li:first-child {
  color: orange;
}
<ul>
<li>lorem</li>
  <li>lorem</li>
  <li>lorem</li>
  <li>lorem</li>
</ul>
````


### Kaynak:

[Patika.dev](https://app.patika.dev/moduller/css/css-seciciler-ile-calismak,-i%CC%87stedigimiz-html-etiket-yapisina-ozelliklik-ekleyebilmek)