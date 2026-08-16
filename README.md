# Samsung ZIP Channel List Editor
## Samsung ZIP Kanal Listesi Düzenleyici

Browser-based editor for Samsung satellite channel lists stored in `Channel_list_*.zip` exports.

Samsung `Channel_list_*.zip` dosyalarındaki uydu kanallarını tarayıcı üzerinden düzenlemek için hazırlanmış açık kaynak web editörü.

## Live Demo / Canlı Demo

**https://lukama1.github.io/samsung-channel-list-editor/**

## Türkçe

### Özellikler
- Samsung `Channel_list_*.zip` dosyasını tarayıcıda açar; dosya sunucuya yüklenmez.
- `dvbs` SQLite veritabanındaki DVB-S / uydu kanallarını listeler.
- **Tümü / TV / Radyo** sekmeleriyle yalnız istenen kanal türünü gösterir.
- Şifreli / şifresiz filtreleme ve kanal adı araması yapar.
- Tekli seçim, checkbox ile toplu seçim ve **Shift + tıklama ile aralık seçimi** destekler.
- Görünen kanalların tamamını veya ilk N kanalı tek seferde seçebilir.
- Seçilen kanalları birlikte sürükleyip taşıyabilir, başa veya sona alabilir.
- Kanal numarasına veya kanal adına göre sıralayabilir.
- Filtrelenmiş/görünen listeyi seçilen başlangıç numarasından yeniden numaralandırabilir.
- **Aratarak Sıra Oluştur** penceresinde kanal arayıp istediğiniz sırayı oluşturabilir, yukarı/aşağı taşıyabilir ve listenin başına uygulayabilirsiniz.
- **Seçilenleri Sil** ve kaydetmeden önce **Seçilenleri Geri Al** işlevleri vardır.
- Silinen kanalları ayrıca gösterip gizleyebilirsiniz.
- Türkçe / İngilizce arayüz bulunur.
- ZIP başarıyla açılınca giriş ve yükleme alanı kapanır.
- Düzenlenmiş liste tekrar Samsung ZIP biçiminde kaydedilir.

### Silme işlemi

Samsung ZIP/SQLite formatında silme işlemi kaydetme sırasında kanalın `srvId` değerine referans veren ilgili SQLite tablolarından kaydı kaldırır. Bu yaklaşım ChanSort'un Samsung ZIP kaydetme mantığıyla uyumludur. Silme işlemi ZIP kaydedilene kadar arayüzden geri alınabilir.

### Samsung TV uyumluluğu

Uyumluluk model yılından çok TV'nin dışa aktardığı kanal listesi biçimine bağlıdır.

```text
Channel_list_*.zip
├── dvbs        # SQLite
├── sat         # SQLite (varsa)
└── metadata.xml
```

`dvbs` içinde `CHNL`, `SRV` ve `SRV_DVB` tabloları beklenir.

- **2015 ve sonrası:** Samsung J serisiyle yaygınlaşan ZIP + SQLite biçimini kullanan TV'ler tipik hedeftir.
- ChanSort aynı temel Samsung ZIP yapısını **en az 2022 model yılına kadar** kullanılan biçim olarak belgeler.
- **2022 sonrası:** Aynı SQLite yapısı korunuyorsa çalışabilir.
- **2014 ve daha eski:** Birçok model `.scm` / `map-*` biçimi kullanır; bu editör `.scm` desteklemez.

Her zaman TV'den alınan orijinal ZIP dosyasının dokunulmamış bir yedeğini saklayın.

## English

### Features
- Opens Samsung `Channel_list_*.zip` exports locally in the browser; the file is not uploaded.
- Reads DVB-S / satellite channels from the `dvbs` SQLite database.
- **All / TV / Radio** tabs filter the list by service type.
- Search plus encrypted/free-to-air filtering.
- Single selection, checkbox multi-selection and **Shift-click range selection**.
- Select all visible channels or the first N channels.
- Drag selected channels as a group, or move the selection to the top/bottom.
- Sort by channel number or name.
- Renumber the current filtered/visible order from a chosen starting number.
- **Build Order by Searching** lets you search channels, create a custom sequence, move entries up/down and apply it to the top of the list.
- **Delete Selected** and **Restore Selected** before saving.
- Show/hide channels marked for deletion.
- Turkish / English interface.
- The introduction/upload area collapses after a valid ZIP opens.
- Saves the modified database back into a Samsung ZIP archive.

### Deletion

When saving, deleted services are removed from SQLite tables that reference their `srvId`. This follows the same general physical-deletion approach used by ChanSort's Samsung ZIP serializer. Deletions remain reversible in the UI until the modified ZIP is saved.

### Compatibility

Expected structure:

```text
Channel_list_*.zip
├── dvbs
├── sat
└── metadata.xml
```

The `dvbs` database is expected to contain `CHNL`, `SRV` and `SRV_DVB`.

- **2015 and newer:** Typical target for the ZIP + SQLite format introduced around Samsung J-series.
- ChanSort documents this Samsung ZIP format through **at least model year 2022**.
- **After 2022:** May work when the same SQLite structure is retained.
- **2014 and older:** Many TVs use `.scm` / `map-*`; `.scm` is not supported by this project.

Always keep an untouched backup of the original TV export.

## References / Kaynaklar

Interface/workflow ideas such as bulk selection and search-based ordering were studied from the open-source SCM editor by Sezer İltekin:

- https://github.com/iltekin/scm-editor
- https://iltekin.github.io/scm-editor/

Samsung ZIP/SQLite compatibility and database-save behavior were cross-checked against ChanSort:

- https://github.com/PredatH0r/ChanSort

This project implements its own Samsung ZIP/SQLite handling and does not copy the SCM file parser, because `.scm` and Samsung ZIP/SQLite are different formats.

## Privacy / Gizlilik

The selected channel-list archive is processed locally in browser memory. JSZip and sql.js are loaded from jsDelivr CDN.

Kanal listesi tarayıcı belleğinde yerel olarak işlenir. JSZip ve sql.js kütüphaneleri jsDelivr CDN üzerinden yüklenir.

## Disclaimer / Sorumluluk reddi

This project is not affiliated with, sponsored by, or endorsed by Samsung Electronics. Channel-list formats can vary by model and firmware.

Bu proje Samsung Electronics ile bağlantılı değildir ve Samsung tarafından onaylanmamaktadır. Kanal listesi biçimleri model ve firmware'e göre değişebilir.