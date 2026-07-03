# Kullanılan Promptlar (Vibe Coding)

---

### 1. Konu Seçimi ve Proje Planı
> Finans & Ekonomi temasında bir veri bilimi dönem projesi yapmak istiyorum. Fikrim,
> Borsa İstanbul'daki büyük şirketlerin dolar kuru ve altın fiyatındaki değişimlere ne
> kadar duyarlı olduğunu incelemek. Bu konuyu, nedensellik iddiasına girmeden, ölçülebilir
> ve savunulabilir bir araştırma sorusuna nasıl daraltabilirim? Bana önerilen kapsamı ve
> uçtan uca iş akışını (veri kaynağı, temizleme, EDA, modelleme) adım adım özetle.

### 2. Veri Kaynağı ve Hisse Seçimi
> BIST30 içinden, işlem hacmi en yüksek ve farklı sektörleri temsil eden 12 blue-chip
> (öncü) hisse seçmek istiyorum. Bu hisseleri, USD/TRY kurunu ve ons altını 2021–2026
> aralığında `yfinance` API'si ile çekecek, doğru Yahoo Finance sembollerini (`.IS` uzantısı
> dahil) kullanan bir Python scripti hazırla. Ham veriyi CSV olarak kaydetsin.

### 3. Veri Temizleme ve Optimizasyon
> Çektiğim veride BIST ile ABD piyasasının tatil günleri farklı olduğu için tarih boşlukları
> oluşuyor. Verileri BIST işlem günlerine hizala, makro serilerdeki (dolar/altın) boşlukları
> forward-fill ile doldur, tip dönüşümlerini yap ve eksik değer kalmadığını doğrula. Ayrıca
> fiyat serilerinin durağan olmaması nedeniyle analizi günlük getiri (yüzde değişim) üzerine
> taşı ve nedenini kısaca açıkla.

### 4. Keşifsel Veri Analizi (EDA)
> Temizlenmiş veri seti üzerinde keşifsel analiz yap. En az dört farklı görselleştirme türü
> kullan: normalize edilmiş fiyat çizgi grafiği (log ölçek), getiri korelasyonu ısı haritası,
> risk–getiri saçılım grafiği ve yuvarlanır (rolling) korelasyon zaman serisi. Her grafiğin
> altına, bulguyu tema bağlamında yorumlayan kısa bir not ekle.

### 5. Araştırma Sorularının Tanımlanması
> Hocanın zorunlu kapsamına göre en az üç somut araştırma sorusu tanımlamam gerekiyor.
> Elimdeki veriyle (hisseler + dolar + altın) yanıtlanabilecek, birbirini tamamlayan üç
> araştırma sorusu öner ve her birinin hangi yöntemle (regresyon, aykırı değer analizi,
> gecikmeli korelasyon) yanıtlanacağını belirt.

### 6. Modelleme — Regresyon (AS-1)
> Her hisse için `getiri = α + β(USD)·dolar_getirisi + β(altın)·altın_getirisi + ε`
> biçiminde bir OLS regresyonu kur. `statsmodels` kullanarak her hissenin dolar betasını,
> p-değerini ve R² değerini bir tabloda topla; istatistiksel olarak anlamlı (p<0,05)
> katsayıları vurgulayan bir bar grafiği üret. Sonucu sektörel duyarlılık bağlamında yorumla.

### 7. Aykırı Değer / Dolar Şoku Analizi (AS-2)
> Doların günlük getirisinin en yüksek %5'lik dilimine giren günleri "dolar şoku günü" olarak
> tanımla. Bu uç değerleri silmeden, ihracatçı ve banka gruplarının şok günlerindeki ortalama
> getirilerini normal günlerle karşılaştır. Ayrışmayı gösteren bir görsel üret ve sonucu
> regresyon bulgusuyla ilişkilendir.

### 8. Öncülük / Gecikmeli İlişki Analizi (AS-3)
> Dolar getirisi ile hisse getirileri arasında –5 ile +5 iş günü aralığında gecikmeli çapraz
> korelasyon hesapla. Doların mı hisseleri, hisselerin mi doları öncelediğini; ilişkinin
> eşzamanlı mı yoksa gecikmeli mi olduğunu değerlendiren bir görsel ve yorum hazırla.

### 9. Kısa Rapor Oluşturma
> Tüm bulguları, hocanın istediği yapıya uygun 3–5 sayfalık bir Word raporuna dönüştür:
> problem tanımı, kullanılan veri seti ve kaynağı, yöntem (veri temizleme/optimizasyon
> vurgulu), bulgular, sınırlamalar ve öğrenilenler. Vurgu ekonomik teori değil, veri bilimi
> sürecinin kendisi olsun. Anahtar grafikleri ve regresyon tablosunu rapora göm.

### 10. Teslim: Notebook, README ve Sürüm Kontrolü
> Teslim için: (a) veri yükleme, temizleme, EDA ve modellemenin tamamını içeren, her kod
> bloğu yorumlarla açıklanmış tek bir çalışır notebook üret; (b) proje ekibi bilgisi,
> çalıştırma talimatları, kullanılan kütüphaneler ve veri kaynağı/lisansını içeren bir README
> hazırla. Ardından bu dosyaları git ile bir commit'e ekleyip GitHub deposuna push et.
