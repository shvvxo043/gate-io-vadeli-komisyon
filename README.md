# gate io vadeli işlemler: komisyon tablosu, kaldıraç ayarı ve ilk emri sıfırdan açma rehberi

Bu aramayı yapan çoğu kişinin kafasında iki soru var: "Kaldıraçlı işlem tam olarak nasıl açılıyor?" ve "Bu iş bana kaça mal oluyor?" İkinci sorunun cevabı, çoğu rehberin atladığı üç sayıya bakıyor — kademe komisyonun, kaldıracın ve fonlama oranın. Bunları bilmeden açılan bir pozisyon, yönü doğru olsa bile maliyetle eriyebiliyor.

Aşağıda Gate.io'nun (artık Gate.com) vadeli işlem tarafını baştan sona geçiyorum: hangi sözleşme tipleri var, maker/taker komisyonu nasıl işliyor, VIP kademeleri hangi eşiklerde açılıyor, kaldıraç neden "125x var" diye kullanılmıyor ve ilk emri hangi sırayla açman gerekiyor. Rakamlar Gate'in kendi ücret ve yardım sayfaları ile bağımsız incelemelerden karşılaştırılarak yazıldı; yerdeğiştiren parametreler için hangi sayfanın geçerli olduğunu da belirtiyorum.

## Gate.io vadeli işlemler hangi ürünleri kapsıyor

Gate'in türev tarafında üç ayrı yapı var ve yeni başlayanların ilk karıştırdığı nokta tam olarak burası.

**USDT-marjinli perpetual (U-marjinli).** Teminat ve kâr/zarar USDT üzerinden. Cüzdanında USDT olduğu sürece onlarca farklı coinin sözleşmesini aynı hesaptan açabiliyorsun. Pratikte en çok kullanılan taraf bu.

**Coin-marjinli (ters/coin-marjinli) perpetual.** BTC, ETH gibi coinlerle teminat yatırıyorsun, kâr-zarar da o coin üzerinden hesaplanıyor. Cüzdanındaki BTC'yi satmadan uzun pozisyon taşımak isteyenler bunu kullanıyor. Karşılığında kur riski ve ekstra çevrim maliyeti geliyor.

**Vadeli (delivery) sözleşmeler.** Bunların gerçek bir bitiş tarihi var: haftalık, gelecek hafta, ay sonu, çeyrek sonu gibi döngüler. Vade dolmadan pozisyonu kapatman ya da bir sonraki vadeye taşıman gerekiyor. Uzun süre pozisyon taşımak istiyorsan perpetual daha az baş ağrısı çıkarıyor.

| Ürün | Teminat ve hesaplama | Vade | Kime uygun |
| --- | --- | --- | --- |
| USDT-marjinli perpetual | USDT | Yok | Çoğu kullanıcının standart tercihi |
| Coin-marjinli (ters) perpetual | BTC, ETH vb. | Yok | Cüzdanındaki coini bozmak istemeyenler |
| Vadeli (delivery) sözleşme | USDT | Hafta / ay / çeyrek sonu | Vade yapısı üzerinden işlem kurgulayanlar |

USDT-marjinli ile coin-marjinli arasındaki farkı Gate de iki ayrı ürün olarak ele alıyor; ikisinin de perpetual (yani süresiz) sürümü ve delivery sürümü mevcut.

👉 [Gate.io'da vadeli işlem hesabını buradan açabilirsin](https://bit.ly/GateVIP)

## Komisyon tarafı: ne zaman kesilir, ne kadar ödersin

Gate'in yardım sayfasının açıkça belirttiği bir nokta var: vadeli işlem ücreti sadece pozisyon açarken, kapatırken veya azaltırken kesiliyor. Bekleyen bir emir dolmadıysa ya da iptal edildiyse ücret yok. Ücret pozisyonun **değeri** üzerinden hesaplanıyor, kaldıraçtan bağımsız. Yani 10x ile de 50x ile de aynı büyüklükte bir pozisyonun komisyonu aynı çıkıyor — kaldıraç riski büyütüyor, komisyonu değil.

İki tarife var:

- **Maker (yapan):** Emrin anında dolmuyor, emir defterinde bekliyor ve birileri gelip seninle eşleşiyor. Piyasaya likidite eklediğin için oran düşük. Puan (point) ile maker komisyonu ödenemiyor.
- **Taker (alan):** Emrin anında defterdeki mevcut emirlerle eşleşiyor. Likiditeyi azalttığın için oran yüksek.

Hesap basit: **Ücret = Pozisyon değeri × (maker veya taker oranı)**. 100 USDT'lik bir piyasa emri VIP 0 oranıyla 100 × %0,05 = 0,05 USDT komisyon üretiyor. Tabloyu ezberlemeye gerek yok, mantık bu.

### VIP kademeleri: tüm oranlar tek tabloda

Aşağıdaki tablo USDT-marjinli perpetual oranları. Kademe yükseldikçe maker tarafı önce sabit kalıyor, sonra düşüyor ve VIP 15'te sıfıra iniyor; taker tarafı ise kademeli azalıyor.

| Kademe | 30 günlük işlem hacmi eşiği | Maker | Taker | Hesap |
| --- | --- | --- | --- | --- |
| VIP 0 | 0 USD | %0,020 | %0,050 | [Kayıt ol](https://bit.ly/GateVIP) |
| VIP 1 | 60.000 USD | %0,020 | %0,050 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 2 | 120.000 USD | %0,020 | %0,050 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 3 | 240.000 USD | %0,020 | %0,048 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 4 | 500.000 USD | %0,020 | %0,048 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 5 | 1.000.000 USD | %0,020 | %0,045 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 6 | 3.000.000 USD | %0,018 | %0,042 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 7 | 8.000.000 USD | %0,016 | %0,0375 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 8 | 20.000.000 USD | %0,014 | %0,035 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 9 | 50.000.000 USD | %0,012 | %0,032 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 10 | 100.000.000 USD | %0,010 | %0,030 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 11 | 120.000.000 USD | %0,008 | %0,028 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 12 | 240.000.000 USD | %0,006 | %0,026 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 13 | 440.000.000 USD | %0,005 | %0,024 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 14 | 800.000.000 USD | %0,002 | %0,022 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 15 | 1.600.000.000 USD | %0 | %0,018 | [Kademe detayı](https://bit.ly/GateVIP) |
| VIP 16 | 3.000.000.000 USD | %0 | %0,016 | [Kademe detayı](https://bit.ly/GateVIP) |

Tabloda göze çarpan birkaç şey var. VIP 1 ve VIP 2, hacim eşiğini aşıyor ama oranı hiç değiştirmiyor — sadece maker tarafı belli bir yerden sonra hareket ediyor. Gerçek kopuş VIP 6'dan sonra başlıyor. Kademe 16'ya ulaşmak 3 milyar dolarlık 30 günlük hacim istiyor; bu bir bireysel kullanıcı senaryosu değil, masa/market maker seviyesi.

### Hacim nasıl sayılıyor? Vadeli işlemin ağırlığı düşük

Bu, insanların en çok yanıldığı yer. Gate kademe hesabında tüm hacmi eşit saymıyor:

- Spot işlem hacmi (convert dahil) %100 sayılıyor
- USDT perpetual, BTC perpetual ve USDT delivery vadeli işlemleri %40 sayılıyor
- USD1 sözleşmeleri ve opsiyonlar %20
- CFD sözleşmeleri %10

Yani vadeli işlemde 100.000 dolarlık hacim yapmak, kademe hesabında 40.000 dolar gibi işleniyor. Kademe atlamak isteyen bir vadeli işlem kullanıcısının spot tarafta da hacim üretmesi ya da diğer kademe yolunu kullanması gerekiyor. O diğer yol da var: 30 günlük hacim yerine 14 günlük ortalama GT varlığı ya da hesap değeri üzerinden de kademe atanabiliyor. Örneğin VIP 1 için 100 GT veya 2.000 USD hesap değeri, VIP 4 için 2.500 GT veya 20.000 USD, VIP 8 için 50.000 GT veya 400.000 USD gibi eşikler tanımlı. Kademe ayda bir yeniden hesaplanıyor ve iki yoldan hangisi avantajlıysa o geçerli oluyor.

Sadece vadeli işlem yapan biri için gerçekçi tablo şu: ilk ciddi indirim VIP 6'da (taker %0,042), hissedilir eşik VIP 10'da (%0,030) geliyor. Ona kadar ödediğin şey standart %0,05 taker oranı.

### Puan (point) ile taker komisyonunu düşürmek

Gate'in puan sistemi vadeli işlem komisyonuna mahsup edilebiliyor ama tek tarafta: taker ücretleri puanla kapatılabiliyor, maker ücretleri kapatılamıyor. Puan mahsubu %0,075 sabit oranı üzerinden hesaplanıyor ve koşullara bağlı indirimlerle birleşik oran en düşük %0,0225'e kadar inebiliyor. Spot tarafta GT ile ödeme indirimi ayrıca var; vadeli işlemlerde asıl kaldıraç (mecazi) VIP kademesi ve puan mahsubu.

## Kaldıraç: 125x görmek 125x kullanmak anlamına gelmiyor

Gate'in kendi eğitim dokümanı, izole modda pozisyon kaldıracının 1x ile 125x arasında ayarlanabildiğini söylüyor. Bağımsız incelemeler ise gerçek üst sınırın işlem çiftine ve pozisyon büyüklüğüne göre değiştiğini gösteriyor: BTC ve ETH perpetual'ında üst sınır yüksek (100x civarı) ama sadece küçük pozisyon büyüklüklerinde; pozisyon büyüdükçe risk limit kademeleri kaldıracı otomatik aşağı çekiyor. Orta ve küçük piyasa değerli coinlerde tavan genelde 10x–25x bandında kalıyor.

Gate bunu zaten açıkça yazıyor: fonlama oranı, minimum fiyat adımı, maksimum kaldıraç, risk limitleri ve sürdürme teminatı piyasa koşullarına göre gerektiğinde ayarlanıyor. Yani "BTC'de 125x var" cümlesi bir reklam cümlesi, bir taahhüt değil.

Teminat modu seçimi kaldıraçtan daha çok fark yaratıyor:

**İzole marjin.** Açtığın pozisyona sabit bir teminat ayrılıyor. Zarar o teminatla sınırlı kalıyor; likidasyon diğer pozisyonlara ve hesabındaki diğer bakiyeye dokunmuyor. Birden fazla pozisyon taşıyorsan pratik seçim bu.

**Cross (çapraz) marjin.** Hesabındaki tüm kullanılabilir bakiye ortak teminat oluyor. Sermaye verimliliği daha yüksek ama bir pozisyondaki büyük zarar diğerlerini de sürüklüyor. Yeni başlayan biri için ilk tercih değil.

## Fonlama oranı: vadeli işlemin görünmez kirası

Perpetual sözleşmelerin fiyatını spot fiyata yakın tutmak için fonlama oranı mekanizması var. Mantık basit: uzun pozisyonlar ağır bastığında long'lar short'lara ödüyor, short'lar ağır bastığında short'lar long'lara ödüyor. Aracı yok, ödeme kullanıcılar arasında.

Ödeme aralığı sözleşmeye göre değişiyor. Gate'in eğitim içeriği fonlama ödemesinin genelde 4 veya 8 saatte bir yapıldığını belirtiyor; BTC perpetual'ında yaygın aralık 8 saat. Buradaki tehlike şu: yatay piyasada pozisyon taşırken fonlama oranı saatler içinde işlem komisyonunun katlarına çıkabiliyor. Yönü doğru tahmin edip pozisyonu doğru yöneten biri, fonlama taşıması yüzünden sıfıra yakın bir sonuçla çıkabiliyor.

Pratik kural: pozisyon açmadan önce fonlama oranına ve bir sonraki ödeme saatine bak. Uzun süre taşımayı düşünüyorsan bu maliyeti senaryo hesabına ayrı bir kalem olarak ekle. Sürekli pozitif fonlama tek başına bir sinyal değil ama aşırı iyimserliğin işareti olabilir; short tarafın taşındığı dönemler de aynı derecede dikkat gerektiriyor.

## İlk vadeli işlemi açmak: uçtan uca akış

1. **Hesap aç ve kimlik doğrulamayı tamamla.** Vadeli işlem ve para çekme için kimlik doğrulaması şart. Kayıt linki üzerinden açtığın hesabın içinde davet kodu tanımlı geliyor; yeni kullanıcı görev ve ödül kampanyaları hesabının kampanya sayfasında görünüyor, koşullar dönemsel olarak değişiyor.
2. **Teminatı transfer et.** Vadeli işlem hesabı spot cüzdandan ayrı. Web'de transfer butonu üzerinden, uygulamada Cüzdan > Vadeli İşlem Hesabı yolundan USDT aktarıyorsun. Vadeli işlem hesabına para koymadan emir açamazsın.
3. **Çift seç.** Vadeli işlem sayfasında sol üstteki çift seçici üzerinden işlem yapmak istediğin coinin perpetual ya da delivery sözleşmesini seçiyorsun.
4. **Teminat modunu ve kaldıracı ayarla.** İzole veya cross, ardından kaldıraç çarpanı. Yeni başlayan için mantıklı başlangıç izole mod + düşük kaldıraç. Kaldıraç, likidasyon fiyatını mevcut fiyata yaklaştırmaktan başka bir şey yapmıyor; kâr potansiyelini büyüttüğünü düşünüyorsan yanlış yerdesin.
5. **Emir tipini seç.** Limit emri belirlediğin fiyattan bekler, piyasa emri en iyi mevcut fiyattan anında dolar, koşullu (condition) emirler tetik fiyatına ulaşıldığında devreye girer. Emir defterine girip beklemek istiyorsan limit, gecikme istemiyorsan piyasa.
6. **Yön ve büyüklüğü onayla.** Yön seçimi "al" = long, "sat" = short. Miktarı girerken ekranda gösterilen emir değeri, teminat ve tahmini likidasyon fiyatını oku. Bu üç satırı okumadan onaylayan kişi sayısı az değil.
7. **Daha açmadan stop-loss planla.** Gate'te açılış sırasında ya da pozisyon açıkken kâr al / zarar durdur emirleri tanımlanabiliyor. Pozisyonu kapatmak istediğinde üç yol var: limit fiyattan, piyasa fiyatından veya tek tıkla kapatma. Kâr al ve zarar durdur seviyelerini belirlemeden ekrandan ayrılmak, iyi işlem planının en sık yapılan hatası.

👉 [Gate.io'da vadeli işlem hesabını açıp adımları uygulamalı deneyebilirsin](https://bit.ly/GateVIP)

## Para koymadan denemek: demo hesap

Gate'in bir demo (testnet) hesabı var. Sanal bakiyeyle, gerçek piyasa verisi üzerinden hem spot hem vadeli işlem yapabiliyor; kaldıraç tarafında 125x'e kadar destekliyor. Web ve mobil uygulamadan erişilebiliyor, iOS ve Android uygulamaları üzerinden de kullanılabiliyor.

Bunun sınırları da net. Demo hesapta gerçek likidite kısıtı oluşmuyor, aşırı volatilitede fiyat kayması yaşanmıyor ve psikolojik baskı hiç yok. Emir tiplerini, TP/SL kurulumunu ve pozisyon kapatmayı kas hafızasına almak için iyi bir yer; strateji kârlılığını burada test edip canlıya geçince aynı sonucu beklemek ise klasik bir hata. Sanal bakiyenin periyodik olarak yenilenebildiğini, yani batırmanın bir maliyeti olmadığını da ekleyelim.

## Kopya işlem ve botlar: vadeli işlem tarafında hazır geliyor

Gate'in yeni perpetual duyurularında iki hizmeti ayrıca belirtmesi dikkat çekici: kopya işlem (copy trading) ve işlem botları. Yeni listelenen sözleşmelerde bile bu ikisi açılışla birlikte aktif oluyor.

Kopya işlem, başkasının açtığı pozisyonları otomatik taklit etmek. Buradaki en sık hata, getiri geçmişine bakıp pozisyon büyüklüğüne ve kaldıraca bakmadan takip etmek. Kâr eğrisi düzgün görünen bir hesap, tek bir pozisyonda hesabın tamamını riske atmış olabilir. Grid ve DCA tipi botlar ise yatay piyasada mantıklı, tek yönlü güçlü trendde ise teminatı hızla tüketebilen araçlar. İkisi de "karar veren sistem" değil, "verdiğin kararı otomatik uygulayan sistem".

## Likidasyon nerede gelir, nasıl geciktirilir

Likidasyon, teminatın pozisyonu taşımaya yetmediği noktada sistemin pozisyonu zorla kapatması. Üç ana sebep var: yüksek kaldıraç, ani volatilite ve teminatı zamanında eklememek.

Gate, kâr/zarar ve teminat oranı hesabında **mark price** (işaret fiyatı) kullanıyor. Bu fiyat, spot endeks fiyatı ve prim endeksi üzerinden hesaplanıyor — yani tek bir borsada anlık yaşanan iğne hareketlerinin pozisyonunu likide etmesini engellemek için tasarlanmış bir mekanizma. Yine de mark price'ı takip etmek, kalan teminat oranını görmek ve risk limit kademesinin nerede olduğunu bilmek gerekli.

Büyük pozisyonlarda Gate kısmi likidasyon yaklaşımı uyguluyor: pozisyonun tamamını tek seferde kapatmak yerine teminat oranını eşiğin üstüne çekene kadar kademeli olarak azaltıyor. Bu, volatil dönemlerde büyük pozisyonlarda kaymayı sınırlıyor; ama fiyat motorun tepki verebileceğinden hızlı hareket ederse gap riski ortadan kalkmıyor.

## Gate.io vadeli işlemler kimler için mantıklı, kimler için değil

Gate 2013'ten beri faaliyet gösteriyor ve 3.800'den fazla spot çifti ile listeleme genişliği konusunda en geniş borsalardan biri. Vadeli işlem tarafındaki asıl cazibe de buradan geliyor: Binance veya Bybit'te perpetual'ı olmayan orta ve küçük piyasa değerli coinlere kaldıraçlı erişim. Belirli bir altsinim üzerinde tezin varsa ve o coinin sözleşmesi sadece burada listeliyse, tartışma bitiyor.

Ters yönde de net bir tablo var. BTC ve ETH gibi majörlerde açık pozisyon (open interest) Binance ve Bybit'te belirgin şekilde daha yüksek; büyük nominal büyüklükte işlem yapacaksan spread ve piyasa etkisi aleyhine çalışır. ABD'de ikamet eden kullanıcılar platforma erişemiyor ve Gate yaptırım uygulanan bölgelere hizmet vermiyor — hesap açmadan önce kendi bölgenin koşullarını kontrol etmek gerekiyor. Regülasyona tabi türev ürün erişimi arıyorsan da Gate bu kategoride değil.

Şeffaflık tarafında ise Merkle ağacı yöntemiyle yayımlanan rezerv kanıtı ve likidasyon kayıplarını absorbe etmek için kullanılan sigorta fonu var. Fonun büyüklüğünü, borsanın günlük ortalama açık pozisyonuyla karşılaştırmadan "arkamda sigorta var" diye düşünmek doğru değil.

Tek cümlelik editoryal yorum: altsinim odaklı, orta kaldıraçla çalışan ve işlem maliyetlerini takip eden bir kullanıcı için Gate mantıklı bir durak. BTC üzerinde yüksek nominal kaldıraçlı işlem yapacak biri için değil.

## Sık sorulan sorular

### Gate.io'da vadeli işlem komisyonu ne kadar?

Standart (VIP 0) USDT-marjinli perpetual oranı %0,020 maker ve %0,050 taker. VIP 16'da maker %0'a inerken taker %0,016'ya düşüyor. Ücret sadece açılış, kapanış ve pozisyon azaltma işlemlerinde kesiliyor; dolmayan ya da iptal edilen emirden ücret alınmıyor.

### Komisyon kaldıraca göre artıyor mu?

Hayır. Ücret pozisyon değeri üzerinden hesaplanıyor, kaldıraçtan bağımsız. 10x ile açtığın 1.000 USDT'lik pozisyonun komisyonu, 50x ile açtığın aynı büyüklükteki pozisyonla aynı. Kaldıraç likidasyon mesafesini, dolayısıyla riski değiştiriyor.

### Gate.io'da kaldıraç kaça kadar çıkıyor?

Gate'in dokümanlarında izole modda pozisyon kaldıracı 1x–125x aralığında tanımlı. Pratikte üst sınır işlem çiftine ve pozisyon büyüklüğüne göre değişiyor: majör çiftlerde yüksek tavanlar küçük pozisyonlarda geçerli, pozisyon büyüdükçe risk limit kademeleri kaldıracı aşağı çekiyor; küçük piyasa değerli coinlerde tavan çoğu zaman 10x–25x bandında kalıyor.

### Fonlama oranı ne sıklıkla ödeniyor?

Sözleşmeye göre değişiyor; Gate'in eğitim içeriği 4 veya 8 saatlik aralıkları belirtiyor, BTC perpetual'ında yaygın aralık 8 saat. Long ağır bastığında long'lar short'lara, short ağır bastığında short'lar long'lara ödüyor.

### Vadeli işleme başlamak için gerçek para gerekiyor mu?

Hayır. Gate'in demo (testnet) hesabı sanal bakiye ile gerçek piyasa verisi üzerinden spot ve vadeli işlem yapmaya izin veriyor, kaldıraç tarafında 125x'e kadar. Emir tiplerini ve pozisyon yönetimini para riske atmadan denemek için açık bir seçenek.

### Kademe atlamak için ne kadar hacim gerekiyor?

VIP 1 için 30 günlük 60.000 USD hacim yeterli, ama bu kademede oranlar değişmiyor. İlk hissedilir taker indirimi VIP 6'da (3.000.000 USD) geliyor. Vadeli işlem hacmi kademe hesabında %40 ağırlıkla sayıldığı için sadece vadelle kademe atlamak spot işleme göre daha yavaş.

## Toparlarsak

Gate.io'da vadeli işlemin maliyeti tek bir komisyon oranından oluşmuyor. Gerçek toplam üç kalemden çıkıyor: kademene göre değişen maker/taker oranı, pozisyonu taşıdığın süre boyunca işleyen fonlama oranı ve kaldıracın likidasyon mesafesini ne kadar kısalttığı. İlk ikisi hesap gerektiriyor, üçüncüsü ise disiplin.

Yeni başlıyorsan sıra belli: demo hesapta emir tiplerini öğren, canlıda izole mod ve düşük kaldıraçla başla, her pozisyonda zarar durdur seviyesini daha emir açılırken belirle ve fonlama ödeme saatlerini takvime ekle. Kademe ve oran tablosunu da ayda bir kontrol et — Gate bu parametreleri piyasa koşullarına göre güncelliyor.

👉 [Gate.io vadeli işlem hesabını aç ve güncel komisyon oranlarını kendi kademenden kontrol et](https://bit.ly/GateVIP)
