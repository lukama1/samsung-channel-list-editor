# Samsung ZIP Channel List Editor
## Samsung ZIP Kanal Listesi Düzenleyici

Browser-based editor for reordering Samsung satellite channels stored in `Channel_list_*.zip` exports.

Samsung `Channel_list_*.zip` dosyalarındaki uydu kanallarını tarayıcı üzerinden sıralamak için hazırlanmış açık kaynak web editörü.

## Türkçe

### Özellikler
- `Channel_list_*.zip` dosyasını tarayıcıda açar.
- ZIP içindeki `dvbs` SQLite veritabanından kanalları listeler.
- Kanal numarası değiştirme ve sürükle-bırak sıralama yapar.
- Düzenlenmiş listeyi yeniden ZIP olarak kaydeder.
- Kanal dosyası sunucuya yüklenmez; tarayıcı belleğinde işlenir.
- Güvenlik amacıyla yalnız `SRV.major` kanal sıra numarası değiştirilir. Frekans, PID, transponder ve kanal adına dokunulmaz.

### Samsung TV uyumluluğu
Uyumluluk model yılından çok TV'nin dışa aktardığı kanal listesi biçimine bağlıdır.

Beklenen yapı:
```text
Channel_list_*.zip
├── dvbs        # SQLite
├── sat         # SQLite (varsa)
└── metadata.xml
```

`dvbs` içinde `CHNL`, `SRV` ve `SRV_DVB` tabloları beklenir.

- **2015 ve sonrası:** Samsung J serisiyle yaygınlaşan ZIP + SQLite biçimini kullanan TV'ler projenin tipik hedefidir.
- ChanSort'un Samsung ZIP yükleyicisi aynı temel yapıyı **en az 2022 model yılına kadar** kullanılan biçim olarak belgeler.
- **2022 sonrası:** Aynı SQLite yapısı korunuyorsa çalışabilir; yalnız model yılına göre garanti verilemez.
- **2014 ve daha eski:** Birçok model `.scm` / `map-*` biçimi kullanır. Bu sürüm `.scm` desteklemez.
- Firmware/model kombinasyonları farklılık gösterebilir; gerçek ZIP yapısı model yılından daha önemlidir.

Bu sürüm özellikle **DVB-S / uydu kanal sıralaması** için hazırlanmıştır.

### Kullanım
1. TV'de kanal taramasını tamamlayın.
2. Kanal listesini USB'ye dışa aktarın.
3. Web editörünü açın.
4. `Channel_list_*.zip` dosyasını sayfaya bırakın.
5. Kanalları sıralayın.
6. Düzenlenmiş ZIP'i kaydedin.
7. Orijinal ZIP'i yedek olarak saklayın.
8. Düzenlenmiş ZIP'i TV'ye geri aktarın.

## English

### Features
- Opens Samsung `Channel_list_*.zip` exports in the browser.
- Reads channels from the `dvbs` SQLite database.
- Supports direct channel-number editing and drag-and-drop ordering.
- Exports the modified list back to ZIP.
- The TV channel-list file is processed locally in browser memory and is not uploaded to a server.
- For safety, this version only changes the `SRV.major` channel number. It does not alter frequencies, PIDs, transponders or channel names.

### Samsung TV compatibility
Compatibility depends primarily on the exported channel-list format rather than model year alone.

Expected structure:
```text
Channel_list_*.zip
├── dvbs        # SQLite
├── sat         # SQLite (when present)
└── metadata.xml
```

The `dvbs` database is expected to contain `CHNL`, `SRV` and `SRV_DVB` tables.

- **2015 and newer:** TVs exporting the ZIP + SQLite format that became common with Samsung J-series are the typical target.
- ChanSort's Samsung ZIP loader documents the same basic structure through **at least model year 2022**.
- **After 2022:** May work when Samsung retains the same SQLite structure; model year alone is not a guarantee.
- **2014 and older:** Many models use `.scm` / `map-*` formats. This version does not support `.scm`.
- Firmware/model combinations can differ, so the actual exported ZIP structure matters more than the model year.

This build focuses on **DVB-S / satellite channel ordering**.

### Usage
1. Complete the channel scan on the TV.
2. Export the channel list to USB.
3. Open the web editor.
4. Drop the `Channel_list_*.zip` file onto the page.
5. Reorder the channels.
6. Save the modified ZIP.
7. Keep an untouched original ZIP as a backup.
8. Import the modified ZIP back into the TV.

## GitHub Pages
This repository is ready for GitHub Pages. Publish the `main` branch from `/ (root)`.

Public address after Pages is enabled:
`https://lukama1.github.io/samsung-channel-list-editor/`

## Privacy / Gizlilik
The selected channel-list archive is processed locally. JSZip and sql.js are loaded from jsDelivr CDN.

Kanal listesi tarayıcıda yerel olarak işlenir. JSZip ve sql.js kütüphaneleri jsDelivr CDN üzerinden yüklenir.

## Compatibility reference / Uyumluluk kaynağı
Compatibility guidance is based on the reverse-engineered Samsung ZIP support in ChanSort:
https://github.com/PredatH0r/ChanSort

## Disclaimer / Sorumluluk reddi
This project is not affiliated with, sponsored by, or endorsed by Samsung Electronics. Channel-list formats can vary by model and firmware. Always keep an untouched backup.

Bu proje Samsung Electronics ile bağlantılı değildir ve Samsung tarafından onaylanmamaktadır. Kanal listesi biçimleri model ve firmware'e göre değişebilir. Her zaman orijinal dosyanın yedeğini saklayın.
