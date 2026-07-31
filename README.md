# Pennxrate-Datas-ile-Panel-veri-Analizi
Pennxrate Datası Üzerinde Panel Veri Modellerinin Metodolojik Karşılaştırması

### İÇİNDEKİLER ##
-	Amaç
-	Değişkenler ve Panel Verinin Tanıtımı
o	Değişkenlerin açıklaması
o	Özet İstatistikler
o	Grafikler
-	Klasik Modelin 
-	Veride Yatay Kesit Bağımlılığının ve Birim Kök Testleri
-	Sabit Etkiler Modeli
-	Logaritmik Dönüşüm 
-	Birim Kök Testleri ve Modellerin Tekrar Kurulması
o	Bulgular
-	F Testi
-	LR Testi
-	Rassal Etkiler Modeli
-	LM Testi
-	Hausman Testi
o	Model Kararı.
-	Diagnostikler
o	Wald Testi
o	Wooldridge Testi
o	Robust Tahminci Seçimi
-	PARKS-KMENTA Robust Tahmincisi
-	Modellerin Karşılaştırılması ve Sonuç
-	Kaynakça.

-	## AMAÇ ##

Çalışmamızdaki ilk amacımız pennxrate datası üzerinde panel data modellerini metadolojik olarak karşılaştırmak. Klasik Model, Sabit Etkiler Modeli ve PARKS-KMENTA Robust tahmincisi sonrası Sabit etkiler modelinin karşılaştırılması. Bir diğer amacımız ise ppp teorisinin panel veri istatistiksel metodları ile kanıtlanabilir olup olmadığını görmektir.

Ppp Teorisi, özetle, bir ürün ya da servisin bir ülkede ABD'deki dolar karşılığına göre çok daha ucuza satılıyorsa, o ülkenin para biriminin piyasada "değerinin altında" (undervalued) olduğu kabul edilir.
Bu durumda da zamanla dengeleneceği düşünülür (bu sebeple datamız birim kök testleri için uygun bir data haline gelir). Amaçlarımızdan biri de bunu test etmektir.

## DEĞİŞKENLER ##

Çalışmada kullandığımız pennxrate panel datamız, ülkelerin yıllara göre Amerikan dolarına karşı enflasyondan arındırılmış kurlarını ve her ülkeye ait ppp indeksini 1970-2003 yılları arasında yıllık bazda içeren (T=34 < N=151 sebebiyle) kısa türde panel veridir.

Verideki oecd,g7 gibi kukla değişkenler analizde yer almayacağı için onlar çıktıktan sonra kalan sütunlar aşağıdaki gibidir:

Country: Ülke isimleri (string)
Year: Yıllar.
PPP: (Purchasing Power Parity Index) Satın alım gücü indeksi. Farklı ülkelerin para birimlerinin satın alma güçlerini eşitleyen bir ekonomik dönüşüm oranı ve teorisidir.
id: Stata’da analiz yapabilmek adına her ülke için tanımlanan eşsiz sayı.
realxrate: Gerçek(reel, enflasyondan arındırılmış) Döviz Kuru. 
 
## VERİ SETİNİN PANEL YAPISININ STATA’YA TANITILMASI ##
 

•	Stata’nın verdiği ‘strongly balanced’ ibaresiyle tüm ülkelerin aynı zaman dönemi boyunca hiçbir eksik veri olmadan izlendiğini gösterir.
•	Analiz edilen dönem 1970 ile 2003 yılları arasını kapsamaktadır. Veri seti T=34 yıllık bir zaman serisi boyutuna sahiptir.
•	T=34 literatürde ortak bir kanıya varılmamışsa da biz T<N  olduğu için veriyi kısa panel verisi olarak varsaydık ve analizimizi buna göre yaptık.(örneğin; yatay kesit bağımlılığı testinde pesaran testi kullanıldı.)
•	Delta: 1 unit ifadesiyle verilerin yıllık bazda düzenli aktığını gösterir.


 
•	ppp (Satın Alma Gücü Paritesi): Ortalama değeri 664.08, standart sapması ise 18089.86 olarak hesaplanmıştır. Standart sapmanın yüksekliği, ülkeler arasında satın alma gücü paritesi bakımından oldukça yüksek bir varyans (çeşitlilik/eşitsizlik) olduğunu göstermektedir.

•	realxrate (Reel Döviz Kuru): Gözlem süresi boyunca minimum 0.0055 ile maksimum 11.026 arasında değişmekte olup, ortalama değer 0.632, standart sapma ise 0.570 olarak gerçekleşmiştir.

•	country değişkeninin sayısal karşılığı olmadığı için (string/metin formatında olduğundan) gözlem sayısı 0 görünmektedir; ancak bu durum id değişkeni üzerinden kodlanarak çözülmüştür.


## Modellerin Karşılaştırılması ve Sonuç ##
-	Tabloda görüldüğü üzere Robust Tahmincimiz, katsayılar için daha güvenilir t skorları elde etmiş ve şişirilmiş skorlardan arındırmıştır.
-	Veri durağan hale getirildiğinde ppp katsayısının ppp teorisini destekler yönde olduğu görülmüştür.


## KAYNAKÇA ##
Ders Notları,
STATA,
Veri Seti: http://www.stata-press.com/data/r15/pennxrate.dta
Veri setine ulaşmak için use komutu ardından yukarıdaki linkin eklenmesi yeterlidir.
Çalışmada Üretken Yapay Zekadan karar ve kontrol aşamalarında yardım alınmıştır.
Çetin, M. K., Sekreter, M. S., & Mert, M. (2023). The effect of price and security on tourism demand: Panel quantile regression approach. Advances in Hospitality and Tourism Research (AHTR), 11(2), 256-276.
Frankel, J. A., & Rose, A. K. (1996). A panel project on purchasing power parity: mean reversion within and between countries. Journal of international Economics, 40(1-2), 209-224.

