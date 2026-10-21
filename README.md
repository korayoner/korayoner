Önizleme · henüz yayında değil

# github.com/onerkoray

README, GitHub'ın kendi markdown işleyicisinden geçirildi; sağdaki metin GitHub'da birebir böyle görünecek. Profil fotoğrafının iki sürümü ve profil alanlarının değerleri aşağıda.

Profil fotoğrafı: Tavan işareti, açık zemin

## Koray Öner

onerkoray

Türkiye için bordro, vergi, SGK ve emeklilik hesaplayan testli, açık kaynak araçlar. korayoner.dev · npm: hesap-cekirdegi

- KonumTürkiye
- Site[korayoner.dev](https://korayoner.dev)
- X[@korayonerdev](https://x.com/korayonerdev)
- LinkedIn[in/korayoner](https://www.linkedin.com/in/korayoner/)
- ORCID[0009-0005-8730-3577](https://orcid.org/0009-0005-8730-3577)
- YouTube[@onerkoray](https://www.youtube.com/@onerkoray)

onerkoray / README.md

# Koray Öner

Türkiye'de maaş, vergi, SGK ve emeklilik hesaplarını yapan ücretsiz araçlar yazıyorum. Araçlar ve onları anlatan yazılar [korayoner.dev](https://korayoner.dev) üzerinde; hesap motoru ayrı bir paket olarak açık kaynak.

[korayoner.dev](https://korayoner.dev) · [Hakkımda](https://korayoner.dev/hakkimda/) · [In English](https://korayoner.dev/en/) · [Yayınlar (DOI)](https://korayoner.dev/yayinlar/) · [ORCID 0009-0005-8730-3577](https://orcid.org/0009-0005-8730-3577)

## Neden her rakamın bir testi var

Bir hesaplama aracındaki hata ses çıkarmaz. SGK tavanını ya da bir vergi dilimini yanlış girerseniz sayfa yine açılır, tablo yine düzgün görünür; yalnızca sonuç yanlıştır ve bunu kimse fark etmez.

Bu yüzden sitede her yasal parametrenin tek bir kaynağı var. Araçlardaki ve yazılardaki rakamlar o kaynaktan, motor üzerinden yeniden hesaplanıp testle sabitleniyor. Kanun değişip parametre güncellendiğinde eski rakamı taşıyan test kırılıyor, sayfa sessizce eskimiyor.

Bunu öğrenmenin bedeli de oldu: Eylül 2026'da testi olmayan 17 yazıya test yazdım, beşinde toplam altı yanlış ya da tutarsız rakam çıktı. O günden beri testi olmayan yazı yayına girmiyor.

## Bir örnek: maaş neden Temmuz'da artıyor?

Brüt 60.000 TL, 2026, hiç zam yok. Net her ay aynı olmaz:

```
const Bordro = require("hesap-cekirdegi/bordro/motor.js");

Bordro.hesaplaYil(60000, 2026).aylar.map((a) => Math.round(a.net));
// [47357, 47357, 47357, 46657, 44807, 44807, 45133, 45650, 42640, 42640, 42640, 42640]
```

Ay Ne oluyor Net Ocak – Mart Birikmiş matrah %15 diliminde 47.357 TL Nisan Matrah 190.000 TL'yi geçiyor, ayın bir kısmı %20'den 46.657 TL Mayıs – Haziran Tamamı %20 diliminde 44.807 TL Temmuz Asgari ücret istisnası büyüyor (4.211 → 4.538 TL) 45.133 TL Ağustos Matrah 400.000 TL'yi geçip %27'ye giriyor, ama istisna 5.615 TL'ye çıktığı için net yine artıyor 45.650 TL Eylül – Aralık Tamamı %27 diliminde 42.640 TL

Yıllık toplam net 539.685 TL. Bordrosunda Eylül'de 3.000 TL düşüş gören biri için cevap bu tabloda; [Maaşım neden düştü?](https://korayoner.dev/makaleler/maasim-neden-dustu/) yazısı aynı hesabı daha uzun anlatıyor.

## Nasıl kurulu

- **Tek kaynak.** Asgari ücret, SGK taban ve tavanı, vergi dilimleri, istisnalar: hepsi tek bir parametre dosyasında, resmî kaynağıyla. Aynı değerin ikinci bir kopyası CI'da kırmızı.
- **Motor ve test.** Bordro, kıdem, emeklilik, rapor parası, kira geliri ve kredi hesapları bağımlılıksız JavaScript; aynı kod tarayıcıda ve Node.js'te çalışıyor.
- **Her değişiklikte iki yüzü aşkın kontrol.** Mülga maddeye atıf, süresi geçmiş tarihli iddia, birbirine fazla benzeyen sayfa, bozuk yapısal veri: hepsi yayından önce yakalanıyor.
- **Statik site.** Çatı (framework) yok, derleme adımı yok. Python ve Node üreteçleri sayfaları içerik manifestinden yazıyor.
- **Veri cihazdan çıkmıyor.** Hesaplar tarayıcıda yapılıyor. Paylaşılabilir hesap bağlantısı girdiyi adresin `#` kısmında tutuyor; o kısım sunucuya da ölçüme de gitmiyor.
- **Düzeltmeler açık.** Bulunan hatalar tarihiyle [yayın ilkeleri](https://korayoner.dev/yayin-ilkeleri/) sayfasındaki düzeltme günlüğüne yazılıyor.

## Depolar

Depo Ne [hesap-cekirdegi](https://github.com/onerkoray/hesap-cekirdegi) Sitedeki araçların altında çalışan hesap motoru. [npm](https://www.npmjs.com/package/hesap-cekirdegi)'de, MIT lisanslı. [onerkoray.github.io](https://github.com/onerkoray/onerkoray.github.io) korayoner.dev'in kaynağı: sayfalar, üreteçler, testler ve CI.

```
npm install hesap-cekirdegi
npm test --prefix node_modules/hesap-cekirdegi
```

## Araçlardan birkaçı

Araç Sorduğu soru [Brüt Net Maaş](https://korayoner.dev/maas-hesaplama/) 12 ayın neti, dilim geçişleri ve istisnayla [Bordro Denetimi](https://korayoner.dev/bordro-denetim/) Bordromdaki rakamlar doğru mu? [Ne Zaman Emekli Olurum?](https://korayoner.dev/ne-zaman-emekli-olurum/) EYT, 1999–2008 ve 2008 sonrası; borçlanmanın etkisi [Kıdem ve İhbar Tazminatı](https://korayoner.dev/kidem-tazminati-hesaplama/) Tavan ve damga vergisiyle [Rapor Parası](https://korayoner.dev/rapor-parasi-hesaplama/) Hastalık, iş kazası ve doğum raporunda SGK ödeneği [Dilim Kayması](https://korayoner.dev/dilim-kaymasi-hesaplama/) Vergi dilimleri enflasyonun gerisinde kalınca ne kadar fazla vergi ödüyorum? [Kira Geliri Vergisi](https://korayoner.dev/kira-geliri-vergisi-hesaplama/) İstisna, beyan sınırı, götürü ve gerçek gider [Engelli Araç ÖTV İstisnası](https://korayoner.dev/engelli-arac-otv-istisnasi-hesaplama/) Uygunluk, fiyat sınırı, yerli katkı, on yıl kuralı

Hepsi: [korayoner.dev/araclar](https://korayoner.dev/araclar/) (60'tan fazla).

## Son yazılar

- [SGK'ya devlet katkısı kalktı: ne değişti?](https://korayoner.dev/makaleler/sgk-devlet-katkisi-kalkti/)
- [Ocak 2027 zammı en düşük emekli aylığına yansır mı?](https://korayoner.dev/makaleler/en-dusuk-emekli-ayligi-ocak-2027/)
- [Torba yasa 2026–2027: ne var, ne yok](https://korayoner.dev/makaleler/torba-yasa-ne-var-ne-yok/)
- [Doğum parası ne kadar? 24 haftalık iznin hesabı](https://korayoner.dev/makaleler/dogum-parasi-ne-kadar/)
- [Yılın en düşük maaşı hangi ay?](https://korayoner.dev/makaleler/yilin-en-dusuk-maasi-hangi-ay/)

Hepsi: [korayoner.dev/makaleler](https://korayoner.dev/makaleler/)

## Yayımlanmış çalışmalar

Zenodo'da, açık erişimli, DOI'li:

- [Endekslemenin Aritmetiği: Türkiye'de Ücret Vergisi Tarifesinde Dilim Kayması](https://doi.org/10.5281/zenodo.22818390)
- [Ücret Üzerindeki Zorunlu Yükün Biçimi: Türkiye'de Vergi Kamasının Prim Tavanında Kırılması](https://doi.org/10.5281/zenodo.22819021)
- [Türkiye'de Emekliliğin Finansal Matematiği](https://doi.org/10.5281/zenodo.22819909)
- [Akış ve Stok: BES Devlet Katkısının Efektif Getirisi ve 2026 İndiriminin Ufuk Etkisi](https://doi.org/10.5281/zenodo.22852165)
- [Faiz Oranı Değişimlerinin Banka Kârlılığı ve Kredi Büyümesine Etkisi](https://doi.org/10.5281/zenodo.22852342)
- [OECD Verileriyle Türkiye Ekonomisinin Finansal Haritası](https://doi.org/10.5281/zenodo.22819842)
- [Yüksek Enflasyon Ortamında Sermaye Yapısı Kararları ve Finansal Kaldıracın Ölçümü](https://doi.org/10.5281/zenodo.22972368)
- [Gelişmekte Olan Hisse Senedi Piyasalarında Yatırımcı Duyarlılığı ve Arbitraj Sınırları](https://doi.org/10.5281/zenodo.22972569)

## Şu sıralar (Ekim 2026)

- TÜİK enflasyonu açıkladığı saatte emekli ve memur zammı araçlarını kendiliğinden güncelleyen bir hat. Bugün araçlar açıklamadan birkaç saat sonra güncelleniyor; hedef yarım saat.
- 2027'ye geçiş: asgari ücret ve vergi tarifesi açıklandığı gün bütün araçların aynı saatte 2027'ye geçmesi için prova.

## In English

I build free calculators for Turkish payroll, income tax, social security and pensions, and write the articles that explain the rules behind them. The site is in Turkish; there is a short [English overview](https://korayoner.dev/en/).

Every legal parameter lives in a single source file, and every number in the tools and articles is recomputed by the engine and pinned by a test, so a rate that changes in law breaks a test instead of silently going stale. The engine is published as [`hesap-cekirdegi`](https://www.npmjs.com/package/hesap-cekirdegi): dependency-free, no build step, MIT.

## İletişim

Hata bildirimi, öneri ya da iş birliği için: [iletisim@korayoner.dev](mailto:iletisim@korayoner.dev)

[LinkedIn](https://www.linkedin.com/in/korayoner/) · [X](https://x.com/korayonerdev) · [YouTube](https://www.youtube.com/@onerkoray) · [Substack](https://korayoner.substack.com/) · [Medium](https://medium.com/@onerkoray) · [ORCID](https://orcid.org/0009-0005-8730-3577)

## Profil fotoğrafı

GitHub fotoğrafı daire biçiminde kırpar. Sitedeki logo kenarlıklı bir kare kutu olduğu için doğrudan yüklenirse kenarları kesilir; bu yüzden işaret dairenin güvenli alanına yeniden yerleştirildi. Küçük boylar commit listesinde ve yorumlarda görünen hâl.

Açık sürüm 160 pikselAçık sürüm 40 pikselAçık sürüm 20 piksel

**A · Açık (önerim).** Sitenin başlığındaki logo. GitHub'ın koyu temasında da açık bir daire olarak öne çıkar.

Koyu sürüm 160 pikselKoyu sürüm 40 pikselKoyu sürüm 20 piksel

**B · Koyu.** Tarayıcı sekmesindeki simgeyle aynı aile. Açık temada daha güçlü, koyu temada zeminle yakın.

## Profil alanları

Bu alanları GitHub › Settings › Public profile sayfasına yapıştırın. Biyografi 160 karakter sınırının içinde. Konum bilinçli olarak yalnız ülke; şehir yazılmıyor.

| Name | `Koray Öner` |  |
| --- | --- | --- |
| Bio | `Türkiye için bordro, vergi, SGK ve emeklilik hesaplayan testli, açık kaynak araçlar. korayoner.dev · npm: hesap-cekirdegi` |  |
| Company | `(boş bırakın)` |  |
| Location | `Türkiye` |  |
| Website | `https://korayoner.dev` |  |
| Social accounts 1 | `https://x.com/korayonerdev` |  |
| Social accounts 2 | `https://www.linkedin.com/in/korayoner/` |  |
| Social accounts 3 | `https://orcid.org/0009-0005-8730-3577` |  |
| Social accounts 4 | `https://www.youtube.com/@onerkoray` |  |

## Onayınızdan sonra

1. BenREADME'yi `onerkoray/onerkoray` deposuna gönderirim.
2. Benİki deponun açıklamasını düzeltirim: `onerkoray.github.io` kaldırılmış "günlük" araçlardan söz ediyor; `hesap-cekirdegi` eskimiş bir test sayısı taşıyor.
3. SizProfil fotoğrafını yüklersiniz (Settings › Public profile › Profile picture › Upload a photo). GitHub'ın arayüzü fotoğrafı yalnız elle yüklemeye izin veriyor.
4. SizProfil alanlarını yapıştırırsınız. Erişim anahtarımda profil yazma izni yok; ayrıca X adının `korayonerdev` olması da bu adımda düzelir.
5. SizProfilde "Customize your pins" ile `hesap-cekirdegi` ve `onerkoray.github.io` depolarını sabitlersiniz.
