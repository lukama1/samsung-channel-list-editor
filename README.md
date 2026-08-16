# Samsung Channel List Editor
## Samsung Kanal Listesi Düzenleyici

Browser-based Samsung channel list editor supporting both legacy `.scm` exports and newer `Channel_list_*.zip` + SQLite exports.

Eski Samsung `.scm` kanal listeleri ile yeni `Channel_list_*.zip` + SQLite kanal listelerini aynı tarayıcı arayüzünde düzenlemek için hazırlanmış açık kaynak araç.

## Live Demo / Canlı Demo

**https://lukama1.github.io/samsung-channel-list-editor/**

## Desteklenen formatlar / Supported formats

### Samsung `.scm`
Eski Samsung Smart TV modellerindeki `map-SateD` uydu kanal listesini destekler.

- Kanal numarası düzenleme
- TV / Radyo filtreleme
- Şifreli / şifresiz filtreleme
- Çoklu seçim ve Shift ile aralık seçimi
- Seçilenleri başa / sona alma
- Aratarak özel sıra oluşturma
- Seçilen kanalları silme / geri alma
- Toplu silme
- Kayıt checksum değerlerinin yeniden hesaplanması
- Orijinal `.scm` dosya adının korunması

### Samsung `Channel_list_*.zip`
Samsung J serisi (2015) ile yaygınlaşan ve ChanSort tarafından en az 2022 model yılına kadar belgelenen SQLite tabanlı kanal listelerini hedefler.

Beklenen yapı:

```text
Channel_list_*.zip
├── dvbs        # SQLite
├── sat         # SQLite (varsa)
└── metadata.xml
```

`dvbs` içinde `CHNL`, `SRV` ve `SRV_DVB` tabloları beklenir.

## Ortak özellikler / Shared features

- Dosya türünü otomatik algılama (`.scm` / `.zip`)
- Türkçe / İngilizce arayüz
- Tümü / TV / Radyo sekmeleri
- Kanal adı arama
- Şifreli / şifresiz filtreleri
- Görünen kanalları toplu seçme
- İlk N kanalı seçme
- Shift + tıklama ile aralık seçme
- Seçili grubu sürükleyip taşıma
- Numaraya veya isme göre sıralama
- Seçilenleri başa / sona alma
- Görünen listeyi istenen başlangıç numarasından yeniden numaralama
- Aratarak sıra oluşturma
- Seçilenleri silme ve geri alma
- Silinenleri gösterme

## Toplu Silme / Bulk Delete

Toplu Silme menüsünde şu seçenekler bulunur:

- **Tüm TV kanallarını sil** / Delete all TV channels
- **Tüm radyoları sil** / Delete all radio channels
- **Tüm şifreli kanalları sil** / Delete all encrypted channels
- **Tüm şifresiz kanalları sil** / Delete all free-to-air channels
- **Boş isimli kanalları sil** / Delete channels with empty names

Özellikle tarama sonrası listede kalan isimsiz/boş kayıtları tek işlemle temizlemek için `Boş isimli kanalları sil` seçeneği eklenmiştir.

## Privacy / Gizlilik

Kanal listesi dosyası tarayıcı belleğinde işlenir ve bu uygulama tarafından sunucuya yüklenmez. JSZip ve sql.js kütüphaneleri jsDelivr CDN üzerinden yüklenir.

The channel-list file is processed locally in browser memory and is not uploaded by this application. JSZip and sql.js are loaded from jsDelivr CDN.

## Compatibility notes / Uyumluluk notları

- `.scm` desteği eski Samsung Smart TV kanal listelerindeki `map-SateD` yapısına yöneliktir.
- `.zip` desteği Samsung'un SQLite tabanlı `Channel_list_*.zip` formatına yöneliktir.
- Model yılı tek başına kesin uyumluluk göstergesi değildir; asıl belirleyici dışa aktarılan dosya yapısıdır.
- Her zaman TV'den alınmış orijinal dosyanın dokunulmamış bir yedeğini saklayın.

## References / Kaynaklar

SCM formatı ve arayüz davranışları için referans:

- https://github.com/iltekin/scm-editor
- https://iltekin.github.io/scm-editor/

Samsung ZIP / SQLite formatı için referans:

- https://github.com/PredatH0r/ChanSort

## Disclaimer / Sorumluluk reddi

This project is not affiliated with, sponsored by, or endorsed by Samsung Electronics. Channel-list formats can vary by model and firmware.

Bu proje Samsung Electronics ile bağlantılı değildir ve Samsung tarafından onaylanmamaktadır. Kanal listesi formatları model ve firmware'e göre değişiklik gösterebilir.
