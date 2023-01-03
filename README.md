# Haber sitesinden Veri seti oluşturma

## Kullanılan Kütüphaneler
- requests<br/>
- pandas<br/>
- WordCloud<br/>
- CountVectorizer<br/>
- matplotlib<br/>
- Word2Vec<br/>
- BeautifulSoup<br/>

## Yapılan İşlemler
- Öncelikle Dünyahalleri.com sitesinden en az 100 haberin “Link, Başlık, Haber İçeriği, Haber Zamanı” bilgilerini de barındıran veri setimizi oluşturuyoruz. Bunun için BeautifulSoup kullandık. Ardından gerekli kodları yazmaya başladık.
- “columns ile veri setinde bulunmasını istediğimiz bilgileri sütunlarını oluşturduk ardından da elde ettiğimiz bilgileri içerisine yerleştirebileceğimiz dataframe’i df şeklinde oluşturduk. 
- Çektiğimiz verileri kaybetmemek için kaydettiğimiz dataframe’i doldurduktan sonra .xlsx uzantısında excel formda kaydettik. 
- Url adreslerinden verileri daha hızlı bir şekilde çekebilmek için NewSet isminde url parametresi alan bir fonksiyon tanımladık. Haberleri alacağımız sitenin url’sine bağlandıktan sonra ilgili url’nin içeriğini uygun formatta parçaladık.
- Url üzerinden veriyi çekme işlemi tamamladıktan sonra “news.xlsx” isminde verimizi kaydettik ve “df.read_excel(“news.xlsx”) ile kaydettiğimiz veriyi okuyup veriyi temizleme işlemine başladık. 
- Ardından veriyi inceliyor ve word cloud çizerek görselleştiriyoruz.
- Projemizde ek olarak veri setimize eklediğimiz her satırdaki haber metinlerinin kaç harf ve karakterden oluştuğu bilgisini de df’e ekledik. Bu bilgiler ile matplotlib fonksiyonunu kullanarak haber metni kelime sayısı için bir grafik çizdirdik.
![Haber Metni Kelime Sayısı](https://user-images.githubusercontent.com/81531142/210434748-bae30a88-dac2-4063-9bbc-1d95a693710b.png)
- Şimdi de haber metinlerinde en çok geçen popüler kelimelerin ilk 20 tanesini totalde kaç kere geçtiği bilgisini de veren listeleme işlemi yaptık. Gördüğümüz gibi en çok kullanılan kelimeleri listelediğimiz zaman stop words olarak adlandırdığımız pek de anlamlı olmayan kelimeler popüler olarak listelenmekte.
![En Çok Kullanılan 20 Kelime](https://user-images.githubusercontent.com/81531142/210434722-9b042be4-c8e7-4858-ae67-e47579825924.png)
- . İleride yapmak istediğimiz işlemlerin daha doğru sonuçlar vermesini sağlamak için Dolgu Kelimeleri (Stop Words) metnimizden çıkarma işlemini yapmamız lazım. Bu stop words'lerin değerlendirmesini çıkardıktan sonra en popüler 20 kelimenin görseli aşağıdaki grafikteki gibidir.
![Stop Words sonrası En Popüler 20 kelime](https://user-images.githubusercontent.com/81531142/210434734-204733aa-97e4-470b-abd9-3f41cff06d60.png)
-Sonrasında da en çok peşpeşe kullanılan kelime üçlülerini(trigram) listeledik ve matplotlib ile grafiğini çizdirdik.
- Matplotlib ile gerekli işlemleri yaptıktan sonra veri ile Word2Vec modellemesi yapıyoruz. Dfsplit ile metinleri kelime kelime ayırıp bu değişkenin içerisinde sakladık. Daha sonra da modelimizi oluşturup kaydettik. Böylece her seferinde parçalama işlemini yapıp modali oluşturma zahmetinden kurtulmuş olduk. 
- Oluşturduğumuz modelde haberleri filtreleme yapmasını istiyoruz. Bunun içinde veri setimizde seçili bir kelime üzerinde benzer olan 15 kelimeyi ve benzerlik oranını göstermesini sağladık. 
- Burada önemli olan bir diğer husus ise zaman ve performans kısıtlamaları olması nedeniyle işlemlerimizi 60 satır ile sınırlı hale getirmiş olmamız. Ama bu projemizde 250 satır ile veri işlediğimiz için şu an 60 ile sınırlandırmayıp 250 satır ile işlem yaptığımızda işlemlerimiz daha sağlıklı çalışacak. 
- Son olarak da rastgele seçilen 5 kelimeye en yakın 5 kelimeyi w2vec ile bulup dataframe haline getirerek ekrana yazdırıyoruz. 

![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)

## Kübra Nur GÜLER
## Edanur ÖZTEMUR



