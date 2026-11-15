# İkinci Beyin

Claude Code ile kullanılan kişisel bir hafıza klasörü: klasör düzeni, kural dosyaları ve şablonlar. İçi boş
gelir. Asistan her oturumda bu klasörü okur, seni ve projelerini hatırlar, oturum sonunda
öğrendiğini yerine yazar.

Bu depo [avenoxai/avenoxbeyin](https://github.com/avenoxai/avenoxbeyin) projesinin ikinci sürümünden yola çıktı
ve aylarca günlük kullanımda şekillendi. Burada o kullanımdan geriye kalan düzen var; içerik yok. Dosyaları
kendi bilgilerinle sen doldurursun.

## İçinde ne var

```
CLAUDE.md                    Asistanın her oturumda okuduğu ana kurallar
🔮 850-Companion/            Kim: sana dair olan (kimlik, kurallar, ölçü, açık konular)
🧠 500-Knowledge/            Nasıl: kalıcı bilgi ve yöntem; genel şema beyin-haritasi.md
knowledge/                   Raf: oturumlardan damıtılan konu sayfaları
daily/                       Günlük oturum özetleri
projeler/                    Projelerin; her biri hafızasını kendi .beyin/ klasöründe taşır
📋 Templates/                Not ve proje şablonları
📥 000-Inbox/                Hızlı yakalama
📦 900-Archive/              Eskiyenlerin indiği arşiv
```

## Temel fikir: üç katman

Hafıza üç katmandır ve katmanlar birbirine karışmaz. **Kim** sana dair olandır ve projeler bitse de kalır.
**Nasıl** bir projeden çıkan ama ona bağlı olmayan yöntemdir. **Ne** projenin kendisidir ve projeyle birlikte
yaşar. Bir projede bitmiş işin hikayesi tutulmaz; dosyalar yalnız bugün geçerli olanı söyler, geçmiş git'te
durur.

Ayrıntılı şema: [beyin-haritasi.md](🧠%20500-Knowledge/beyin-haritasi.md).

## Nasıl başlanır

1. Bu depoyu kendi özel depona kopyala ("Use this template" ya da indirip yeni bir depo aç). Beynin kişisel
   bilgi taşıyacağı için deponu özel tut. Git şarttır: bitmiş işin geçmişi yalnız orada durur.
2. Klasörü Claude Code ile aç ve şunu yaz: "CLAUDE.md dosyasını oku. Beni tanımak için birkaç kısa soru sor ve
   cevaplarımla Core.md ile Olcu.md dosyalarını doldur."
3. Yeni bir işe başlarken asistana "şablondan `<ad>` projesini aç" de. `📋 Templates/Proje/` klasörünü
   `projeler/<ad>/` altına kopyalar ve `{{AD}}`, `{{AMAC}}` gibi yer tutucuları sana sorarak doldurur.
   Asistanı her düzelttiğinde kuralı `Kurallar.md` dosyasına yazar.

## Ne yok

Bu depo betik ve otomasyon içermez. Açılışta hafızayı kendiliğinden yükleyen, oturumu özetleyen ya da
eskiyen notu arşive indiren araçlar isteyen bunları kendi ihtiyacına göre ekler. Hazır araçlarla gelen bir
kurulum arayan [özgün projeye](https://github.com/avenoxai/avenoxbeyin) bakabilir; onun güncel sürümü buradakinden
farklı bir klasör düzeni kullanır. Bu düzen betiksiz de çalışır: asistan `CLAUDE.md` dosyasını okur ve adımları
kendisi yapar.

## Lisans ve teşekkür

MIT lisansı. Bu çalışmanın temeli olan [AvenoxBeyin](https://github.com/avenoxai/avenoxbeyin) projesini
yayımlayan [Avenox](https://github.com/avenoxai)'a teşekkürler: klasör düzeni ve Companion fikri oradan gelir.
