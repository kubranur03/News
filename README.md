# Haber sitesinden Veri seti oluşturma

## Kullanılan Kütüphaneler
- requests<br/>
- pandas<br/>
- WordCloud<br/>
- CountVectorizer<br/>
- matplotlib<br/>
- Word2Vec<br/>
- BeautifulSoup<br/>
<br/>
<br/>

## Yapılan İşlemler
- Öncelikle Dünyahalleri.com sitesinden en az 100 haberin “Link, Başlık, Haber İçeriği, Haber Zamanı” bilgilerini de barındıran veri setimizi oluşturuyoruz. Bunun için BeautifulSoup kullandık. Ardından gerekli kodları yazmaya başladık. 

<br/>

- “columns ile veri setinde bulunmasını istediğimiz bilgileri sütunlarını oluşturduk ardından da elde ettiğimiz bilgileri içerisine yerleştirebileceğimiz dataframe’i df şeklinde oluşturduk. 

<br/>


- Çektiğimiz verileri kaybetmemek için kaydettiğimiz dataframe’i doldurduktan sonra .xlsx uzantısında excel formda kaydettik.

<br/>


- Url adreslerinden verileri daha hızlı bir şekilde çekebilmek için NewSet isminde url parametresi alan bir fonksiyon tanımladık. Haberleri alacağımız sitenin url’sine bağlandıktan sonra ilgili url’nin içeriğini uygun formatta parçaladık.

<br/>


- Url üzerinden veriyi çekme işlemi tamamladıktan sonra “news.xlsx” isminde verimizi kaydettik ve “df.read_excel(“news.xlsx”) ile kaydettiğimiz veriyi okuyup veriyi temizleme işlemine başladık.

<br/>


- Ardından veriyi inceliyor ve word cloud çizerek görselleştiriyoruz. 

<br/>


- Projemizde ek olarak veri setimize eklediğimiz her satırdaki haber metinlerinin kaç harf ve karakterden oluştuğu bilgisini de df’e ekledik. Bu bilgiler ile matplotlib fonksiyonunu kullanarak haber metni kelime sayısı için bir grafik çizdirdik. 

<br/>
<br/>
### Haber Metni Kelime Sayısı:<br/><br/>

![Haber Metni Kelime Sayısı](https://user-images.githubusercontent.com/81531142/210434748-bae30a88-dac2-4063-9bbc-1d95a693710b.png)

<br/>


- Şimdi de haber metinlerinde en çok geçen popüler kelimelerin ilk 20 tanesini totalde kaç kere geçtiği bilgisini de veren listeleme işlemi yaptık. Gördüğümüz gibi en çok kullanılan kelimeleri listelediğimiz zaman stop words olarak adlandırdığımız pek de anlamlı olmayan kelimeler popüler olarak listelenmekte. <br/>

<br/>
<br/>
### En Çok Kullanılan 20 Kelime:<br/><br/>

![En Çok Kullanılan 20 Kelime](https://user-images.githubusercontent.com/81531142/210434722-9b042be4-c8e7-4858-ae67-e47579825924.png)

<br/>

- İleride yapmak istediğimiz işlemlerin daha doğru sonuçlar vermesini sağlamak için Dolgu Kelimeleri (Stop Words) metnimizden çıkarma işlemini yapmamız lazım. Bu stop words'lerin değerlendirmesini çıkardıktan sonra en popüler 20 kelimenin görseli aşağıdaki grafikteki gibidir.

<br/>
<br/>
### Stop Words sonrası En Popüler 20 kelime:<br/><br/>

![Stop Words sonrası En Popüler 20 kelime](https://user-images.githubusercontent.com/81531142/210434734-204733aa-97e4-470b-abd9-3f41cff06d60.png)

<br/>

-Elde ettiğimiz verileri kullanmak için en popüler kelimelerin bigram (ikililerine) bakalım.
<br/>
<br/>
### En Popüler 20 Bigram:<br/><br/>

![En Popüler 20 Bigram](https://user-images.githubusercontent.com/81531142/210437194-859d1734-10d0-43cf-ae87-82f65f6727c9.png)

<br/>

-Sonrasında da en çok peşpeşe kullanılan kelime üçlülerini(trigram) listeledik ve matplotlib ile grafiğini çizdirdik.
<br/>
<br/>
### En Popüler 20 Trigram:<br/><br/>

![En Popüler 20 Trigram](https://user-images.githubusercontent.com/81531142/210437178-701a190d-1eba-4b34-bd1b-b18d699fd3ad.png)

<br/>

-Daha görsel bir şey yapmak istediğimiz için WordCloud (Kelime Bulutu) işlemi yaptık. Bu görselleştirme metodu en kısa tanımıyla seçilen metinde kelimenin görünüm sıklığını gösterir ve kelimenin boyutunu kelimenin kullanım sıklığına göre değişir. Daha sonra tüm kelimeler bir küme ya da kelime bulutu şeklinde düzenlenir. Alternatif olarak, kelimeler yatay çizgiler, sütunlar veya bir şekil halinde de düzenlenebilir. Bizde elimizdeki veri seti ile haberlerde en çok kullanılan kelimelerin yoğunluğunu baz alan bir kelime bulutu oluşturduk.
<br/>
<br/>
### WordCloud:<br/><br/>

![WordCloud](https://user-images.githubusercontent.com/81531142/210437168-6f41e388-5c12-4b0d-9cf5-f5598f03831b.png)

<br/>

- Matplotlib ile gerekli işlemleri yaptıktan sonra veri ile Word2Vec modellemesi yapıyoruz. Dfsplit ile metinleri kelime kelime ayırıp bu değişkenin içerisinde sakladık. Daha sonra da modelimizi oluşturup kaydettik. Böylece her seferinde parçalama işlemini yapıp modali oluşturma zahmetinden kurtulmuş olduk. 

<br/>

- Oluşturduğumuz modelde haberleri filtreleme yapmasını istiyoruz. Bunun içinde veri setimizde seçili bir kelime üzerinde benzer olan 15 kelimeyi ve benzerlik oranını göstermesini sağladık. 

<br/>

-Yaptığımız modeli test etmek adına şöyle bir örnek yapabiliriz. Gireceğimiz "Dünya" kelimesi ile benzerliği en yüksek olan 15 kelimeyi ve benzerlik oranını getiren bir kod yazalım.
### Test:<br/><br/>

![Test](https://user-images.githubusercontent.com/81531142/210439252-45e2eb9c-8e0f-41f2-b010-2ccabdd74ca6.png)

<br/>

- Burada önemli olan bir diğer husus ise zaman ve performans kısıtlamaları olması nedeniyle işlemlerimizi 60 satır ile sınırlı hale getirmiş olmamız. Ama bu projemizde 250 satır ile veri işlediğimiz için şu an 60 ile sınırlandırmayıp 250 satır ile işlem yaptığımızda işlemlerimiz daha sağlıklı çalışacak. 

<br/>


- Son olarak da rastgele seçilen 5 kelimeye en yakın 5 kelimeyi w2vec ile bulup dataframe haline getirerek ekrana yazdırıyoruz. 

<br/>

- Seçtiğimiz Dünya, Teknoloji, Yapay, Blockchain, Robotik kelimelerine en yakın 5 kelimeyi bulup, bu bulduğumuz verileri bir df içinde tutalım.
<br/>
### En Yakın 5 Kelime:<br/><br/>

![En Yakın 5 Kelime](https://user-images.githubusercontent.com/81531142/210439549-57eb80c7-f90a-413c-9bfa-448c0c3390b4.png)

<br/>


## Kübra Nur GÜLER
## Edanur ÖZTEMUR



