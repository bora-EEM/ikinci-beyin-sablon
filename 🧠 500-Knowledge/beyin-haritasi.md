# Beyin haritası

Beynin genel şeması: hangi klasör ne tutar, hangi dosyayı kim yazar, bir oturum nasıl başlar ve biter. Kök
`AGENTS.md` kısa yönlendiricidir; ayrıntı buradadır ve gerekince okunur.

## Klasörler

| Klasör | Ne tutar |
| --- | --- |
| `📥 000-Inbox/Dump/` | Hızlı yakalama: henüz yeri belli olmayan not, bağlantı, fikir |
| `🔮 850-Companion/` | Kim katmanı: kullanıcıya dair her şey |
| `🧠 500-Knowledge/` | Nasıl katmanı: elle yazılan kalıcı bilgi ve yöntem |
| `knowledge/` | Raf: oturumlardan damıtılan konu sayfaları, fihristi `index.md` |
| `daily/` | Günlük: oturum özetleri, gün başına bir dosya |
| `projeler/` | Projeler; her biri kendi hafızasını `.beyin/` altında taşır |
| `yerel/` | Yalnız bu makineye ait projeler, git dışı |
| `📋 Templates/` | Şablonlar: not ve proje şablonu |
| `📦 900-Archive/` | Arşiv: bir zaman yararlı olmuş ama artık güncel olmayan not ve sayfalar |

## Kim katmanı: `🔮 850-Companion/`

| Dosya | Ne tutar | Ne zaman okunur |
| --- | --- | --- |
| `Core.md` | Asistanın kimliği ve kullanıcının kısa tanımı | Her açılışta |
| `Kurallar.md` | Kullanıcının düzeltmelerinden çıkan kurallar | Her açılışta |
| `Threads.md` | Açık konular, proje başına tek satır | Her açılışta |
| `Last-Session.md` | Son oturumların 3 ile 5 cümlelik özeti | Her açılışta |
| `Olcu.md` | Kullanıcının neyi iyi saydığı, nasıl karar verdiği | Yeni projeye başlarken |
| `Journal.md` | Önemli olaylar ve onlardan çıkan ders | Konusu geçince |
| `Sozluk.md` | Kullanıcıya söylenmeyen sözler ve karşılıkları | Her açılışta |

## Ne katmanı: bir projenin içi

| Dosya | Ne tutar |
| --- | --- |
| `AGENTS.md` | Projenin amacı, bittiğinin ölçüsü, değişmez sınırları, komutları |
| `DURUM.md` | Yalnız şimdi: durum, açık kararlar, sıradaki işler. Kısa kalır |
| `.beyin/Kart.md` | Tek bakışta proje: amaç, nerede, sırada. Açılışta okunan dosya |
| `.beyin/Ozellikler.md` | Çalışan özellikler, her biri kendi başlığında; adıyla aranır |
| `.beyin/Temeller.md` | Geçerli temel kararlar ve elenen yollar |
| `.beyin/Threads.md` | Projenin açık konuları |
| `.beyin/Last-Session.md` | Son oturumun teknik notu |

Bitmiş işin hikayesi hiçbir dosyada tutulmaz; git geçmişinde durur. Dosyalar yalnız bugün geçerli olanı söyler.

## Bir oturumun ritmi

Açılışta asistan Kim katmanının beş dosyasını ve varsa projenin kartını okur. Çalışırken kullanıcının her
düzeltmesi kurala dönüşür. Kapanışta proje dosyaları ve Companion güncellenir, günün özeti `daily/` altına
yazılır, yeniden işe yarayacak konu `knowledge/` rafına girer, sonra commit atılır. Kural şudur: kaydedilmemiş
bir oturum hiç yaşanmamış sayılır.

## Kural nereye yazılır

Her projede geçerli olan kural `🔮 850-Companion/Kurallar.md` dosyasına, tek bir projeye ait olan o projenin
`AGENTS.md` dosyasına yazılır. Genel defter büyüdükçe aynı anlama gelen kurallar birleştirilir, proje kuralına
dönüşenler projesine indirilir.

## Birden fazla makine

Beyin özel bir git deposuyla taşınır: oturum başında çek, anlamlı oturum sonunda commit at ve gönder. `yerel/`
taşınmaz. Kendi deposu olan proje ana depoya girmez, `.gitignore` dosyasına yazılır ve kendi içinde ayrıca
kaydedilir.

## Otomasyon

Bu depo yalnız düzeni ve kuralları taşır; hiçbir betik içermez. Açılışta dosyaları kendiliğinden yükleyen,
oturumu özetleyen ya da eski notu arşive indiren otomasyon isteyen bunu kendi ihtiyacına göre ekler. Düzen
betiksiz de çalışır: asistan kök `AGENTS.md` dosyasını okur ve adımları elle yapar.
