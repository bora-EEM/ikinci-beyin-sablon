# İkinci Beyin

**Yapay zeka asistanın her yeni sohbette seni sıfırdan tanımasın.** İkinci Beyin, Claude Code ile kullanılan bir
hafıza klasörüdür: kim olduğunu, seni nasıl düzelttiğini, projelerinin nerede kaldığını düz Markdown dosyalarında
tutar. Asistan her oturuma bu dosyaları okuyarak başlar, öğrendiğini yerine yazarak bitirir.

Bu depo o klasörün düzenini, kurallarını ve şablonlarını taşır. İçi boş gelir; sen kullandıkça dolar.

Claude Code · Markdown · Git · isteğe bağlı Obsidian · MIT lisansı

---

## Neyi çözer

Bir yapay zeka asistanıyla uzun süre çalışınca aynı üç sorun çıkar:

| Sorun | İkinci Beyin'de |
| --- | --- |
| Her yeni sohbette projeyi baştan anlatırsın | Asistan projenin kartını okur, kaldığı yerden başlar |
| Bir kez düzelttiğin hatayı ertesi gün yine yapar | Her düzeltme o an kurala dönüşür ve her açılışta okunur |
| Notlar biriktikçe çöplüğe döner, önemli olan kaybolur | Dosyalar yalnız bugün geçerli olanı söyler; geçmiş git'te durur |

## Nasıl çalışır

![Hafıza üç katman: Kim, Nasıl, Ne](gorseller/katmanlar.svg)

Hafıza üç katmandır ve birbirine karışmaz. **Kim** sana dair olandır: kuralların, ölçün, açık konuların. Projeler
bitse de kalır. **Nasıl** bir projede öğrenilip başka projede de işe yarayan yöntemdir. **Ne** projenin kendisidir
ve projeyle birlikte yaşar. Her bilgi tek bir yere yazıldığı için asistan neyi nerede arayacağını bilir, aynı bilgi
iki yerde çelişmez.

![Bir oturumun döngüsü: açılış, çalışma, kapanış](gorseller/oturum-dongusu.svg)

Döngünün kuralları kökteki [`CLAUDE.md`](CLAUDE.md) dosyasında yazar. Claude Code bu dosyayı her oturumun başında
kendiliğinden okur; bu yüzden ek bir program kurmak gerekmez.

---

## Kurulum

### Gerekenler

| Ne | Neden | Nereden |
| --- | --- | --- |
| Claude Code | Klasörü okuyup yazan asistan | [claude.com/claude-code](https://claude.com/claude-code) (uçbirim, masaüstü uygulaması ya da VS Code eklentisi) |
| Git | Geçmişi tutar, bilgisayarlar arasında taşır | [git-scm.com](https://git-scm.com/downloads) |
| GitHub hesabı | Yedek ve ikinci bilgisayar için; zorunlu değil | [github.com](https://github.com) |
| Obsidian | Notları görsel olarak gezmek için; zorunlu değil | [obsidian.md](https://obsidian.md) |

Kurulu olduklarını uçbirimde şöyle denetleyebilirsin; ikisi de bir sürüm numarası yazmalı:

```bash
git --version
claude --version
```

### 1. Kendi kopyanı oluştur

**GitHub ile (önerilen).** Bu sayfanın üstündeki **Use this template** düğmesine bas, **Create a new repository**
seç. Depoya bir ad ver ve **Private** işaretle: beynin zamanla kişisel bilgi taşıyacak. Sonra bilgisayarına indir:

```bash
git clone https://github.com/KULLANICI-ADIN/DEPO-ADIN.git ikinci-beyin
cd ikinci-beyin
```

**GitHub'sız.** Sayfanın üstündeki **Code** düğmesinden **Download ZIP** ile indir, istediğin yere aç ve klasörün
içinde git'i başlat:

```bash
cd ikinci-beyin
git init
git add -A
git commit -m "ikinci beyin kuruldu"
```

### 2. Klasörü Claude Code ile aç

Uçbirimde klasörün içindeyken `claude` yaz. Masaüstü uygulamasında yeni oturum açarken klasör olarak
`ikinci-beyin`'i seç. Önemli olan, oturumun bu klasörün **kökünden** açılması: `CLAUDE.md` orada durur.

### 3. Asistanla tanış

İlk oturumda şunu yaz:

> CLAUDE.md dosyasını oku. Beni tanımak için birkaç kısa soru sor ve cevaplarımla Core.md ile Olcu.md
> dosyalarını doldur. Bitince oturumu kapanış kurallarına göre kaydet.

Asistan sana kim olduğunu, ne üzerinde çalıştığını ve nasıl bir dil istediğini sorar, cevaplarını
`🔮 850-Companion/` altına yazar.

### 4. Çalıştığını doğrula

Bu adım, kurulumun gerçekten işlediğini görmenin tek yolu:

1. Aynı oturumda asistana kalıcı bir şey söyle: *"Bundan sonra cevaplarında madde listesi kullanma."*
2. Oturumu kapat, **yeni bir oturum** aç.
3. Sor: *"Benimle ilgili hangi kuralları biliyorsun?"*

Asistan söylediğin kuralı geri okuyorsa beyin çalışıyor. Ne değiştiğini dosyada da görebilirsin:

```bash
git log --oneline -3
git show --stat HEAD
```

`🔮 850-Companion/Kurallar.md` değişmiş görünmeli.

### 5. İlk projeni aç

> Şablondan `hava-uygulamasi` adında yeni bir proje aç. Amacı ve bittiğinin ölçüsünü bana sor.

Asistan `📋 Templates/Proje/` klasörünü `projeler/hava-uygulamasi/` altına kopyalar, `{{AD}}`, `{{AMAC}}` gibi
yer tutucuları sana sorarak doldurur. O projede çalışırken her açılışta önce projenin kartını okur.

### 6. Yedekle (GitHub kullanıyorsan)

Asistan her oturumun sonunda değişiklikleri git'e kaydeder ve uzak depoya gönderir. Elle yapmak istersen:

```bash
git add -A
git commit -m "oturum notları"
git push
```

### İsteğe bağlı: ikinci bilgisayar ve Obsidian

**İkinci bilgisayar.** Aynı depoyu orada da `git clone` ile indir. Asistan her oturumun başında son hali çeker,
sonunda gönderir; iki bilgisayar aynı beyni paylaşır. Yalnız o bilgisayara ait işleri `yerel/` klasörüne koy;
o klasör git'e hiç girmez.

**Obsidian.** Obsidian'da **Open folder as vault** ile `ikinci-beyin` klasörünü seç. Notlar arasındaki
bağlantıları harita olarak görürsün. Obsidian nokta ile başlayan klasörleri (`.beyin/`) göstermez; proje hafızasına
dosya gezgininden ya da asistandan bakılır.

### Sorun çıkarsa

| Belirti | Neden ve çözüm |
| --- | --- |
| Asistan seni tanımıyor gibi davranıyor | Oturum kökten açılmamıştır. Klasörün kökünden yeniden aç ya da *"CLAUDE.md dosyasını oku"* de |
| Kurallar dosyası hiç değişmiyor | Kapanış adımı atlanmıştır. Oturum sonunda *"oturumu kapanış kurallarına göre kaydet"* de |
| İki bilgisayarda farklı notlar var | Bir taraf göndermeden kapanmıştır. Önce `git pull`, sonra çalışmaya başla |
| Emoji içeren klasör adları uçbirimde garip görünüyor | Yalnız görünüştür; dosyalar doğru çalışır. Tırnak içinde yaz: `cd "🔮 850-Companion"` |

---

## Klasörler

```
CLAUDE.md               Asistanın her oturumda okuduğu ana kurallar
🔮 850-Companion/       Kim: kimlik, kurallar, ölçü, sözlük, açık konular, son oturum
🧠 500-Knowledge/       Nasıl: kalıcı yöntem; genel şema beyin-haritasi.md
knowledge/              Raf: tekrar eden konuların sayfaları ve fihristi
daily/                  Günlük oturum özetleri
projeler/               Projelerin; her biri hafızasını kendi .beyin/ klasöründe taşır
📋 Templates/           Not ve proje şablonları
📥 000-Inbox/           Hızlı yakalama
📦 900-Archive/         Güncelliğini yitirmiş ama atılmayan notlar
yerel/                  Yalnız bu bilgisayara ait işler (git dışı)
```

Dosya dosya ayrıntı: [beyin-haritasi.md](🧠%20500-Knowledge/beyin-haritasi.md).

## Bir projenin içi

![Bir projenin içi ve dolu bir proje kartı örneği](gorseller/proje-karti.svg)

Asistan açılışta projenin yalnız kartını okur; beş satırlık bir dosya, bağlamı küçük tutar. Çalışan özellikler
`Ozellikler.md` içinde her biri kendi başlığında durur ve adıyla aranır, baştan sona okunmaz. Geçerli kararlar ve
**elenen yollar** `Temeller.md` içindedir: denenip bırakılan fikir yazılı olduğu için aylar sonra yeniden
denenmez.

---

## Tasarım kararları

Bu düzen [AvenoxBeyin](https://github.com/avenoxai/avenoxbeyin) projesinin ikinci sürümünden yola çıktı ve
aylarca her gün kullanılarak değişti. Değişenlerin her biri yaşanmış bir sorundan geldi:

| Karar | Neden |
| --- | --- |
| Bitmiş işin hikayesi dosyalarda tutulmaz | Notlar "ne yaptık" günlüğüne dönünce asistan bugünü bulmak için geçmişi okumak zorunda kaldı. Dosyalar yalnız şimdiyi söyler; geçmiş git'te durur |
| Kural, kapsamına göre yazılır | Genel kural defteri bir ayda üç katından fazla büyüdü ve yarısı tek projeye ait çıktı. Artık her projede geçerli olan genel deftere, projeye özgü olan projeye yazılır |
| Proje hafızası proje klasöründe | Projeler gelir geçer; projeyle ilgili not proje silinince birlikte gider, beyni kirletmez |
| Elenen yollar da yazılır | Aynı tutmayan fikir haftalar sonra yeniden önerildi. Yazılı ret bunu durdurur |
| Sözlük dosyası | Asistanın kendi uydurduğu teknik adlar kullanıcıya bir şey ifade etmiyordu. Söylenmeyecek sözler ve karşılıkları tek yerde |
| Silmek ile arşive indirmek ayrı | İşe yaramayan not silinir; bir zaman doğru olmuş ama eskiyen not arşive iner. İkisi karışınca ya çöp birikiyor ya bilgi kayboluyordu |

## Kendi beynimde

Bu depo, benim her gün kullandığım beynin içi boşaltılmış halidir. Benim kopyamda düzenin üstünde onu kendiliğinden
işleten betikler de var; burada yer almıyorlar, ama düzenin ne kadar taşıdığını gösteriyorlar:

| Ölçü | Değer |
| --- | --- |
| Kullanım süresi | Ağustos 2026'dan bu yana, 64 farklı günde |
| Git'e kaydedilen oturum ve değişiklik | 1.270'in üzerinde |
| Aynı anda yürüyen proje | 17 |
| Düzeltmelerden çıkan genel kural | 56 |
| Raftaki konu sayfası | 209 |
| Toplam hafıza / açılışta okunan | 407 KB / 15,5 KB |

Son satır düzenin asıl getirisi: hafıza büyüdükçe asistanın her açılışta okuduğu kısım küçük kalıyor, çünkü her şey
tek yerde ve gerekince okunuyor. Benim kopyamdaki ek parçalar şunlar: geceleri günlükleri konu sayfalarına işleyen
ve eskiyen notu arşive indiren bir döngü, konusu geçince ilgili notu hatırlatan bir kanca ve asistanın kendi özetini
geçmiş düzeltmelerden oluşan bir sınavla denetleyen bir kontrol.

---

## Sık sorulanlar

**Notlarım nerede duruyor?** Yalnız senin bilgisayarında ve kendi git deponda, düz Markdown dosyaları olarak.
Asistan çalışırken okuduğu dosyalar kullandığın yapay zeka hizmetine gönderilir; bu, Claude Code'u kullanmanın
olağan hali.

**Claude Code dışında çalışır mı?** Düzen düz dosyalardan oluştuğu için ana kural dosyasını okuyabilen her asistanla
kullanılabilir; ben yalnız Claude Code ile kullanıyorum.

**Ek ücret ya da sürekli açık bir hizmet var mı?** Yok. Claude Code aboneliğin dışında hiçbir şey gerekmez.

**Her şeyi kendiliğinden hatırlar mı?** Hayır. Asistan yalnız dosyalara yazılanı hatırlar. Kapanış adımı bu yüzden
önemli: kaydedilmemiş bir oturum hiç yaşanmamış sayılır.

## Lisans ve teşekkür

MIT lisansı, ayrıntısı [LICENSE](LICENSE) dosyasında. Bu çalışmanın temeli olan
[AvenoxBeyin](https://github.com/avenoxai/avenoxbeyin) projesini yayımlayan [Avenox](https://github.com/avenoxai)'a
teşekkürler: klasör düzeni ve Companion fikri oradan gelir.
