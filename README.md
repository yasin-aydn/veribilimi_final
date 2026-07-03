# BIST Blue-Chip Şirketlerinin Dolar ve Altına Duyarlılığı

Veri Bilimi Dönem Projesi — BIST30'da yer alan, işlem hacmi en yüksek 12 blue-chip (öncü)
şirketin günlük getirilerinin dolar kuru (USD/TRY) ve altın fiyatı ile ilişkisinin
incelenmesi. Dönem: 2021–2026, 1.250 işlem günü.

---

| Öğrenci Numarası | Adı Soyadı |
|------------------|------------|
| `1306230017`   | `Yasin Aydın` |

**Ders:** `Veri Bilimi`
**Dönem:** `2025–2026 Bahar`

---

## Araştırma Soruları

- **AS-1:** Hangi sektörler dolara/altına daha duyarlıdır? (doğrusal regresyon)
- **AS-2:** Dolar şoku (aykırı) günlerinde hisseler nasıl ayrışır? (ihracatçı vs banka)
- **AS-3:** Dolar mı hisseyi, hisse mi doları önceller? (gecikmeli çapraz korelasyon)

## Temel Bulgular

- İhracat ağırlıklı sektörler (cam, savunma, demir-çelik, rafineri) dolara **pozitif ve
  istatistiksel olarak anlamlı** duyarlıdır; bankalar tepkisiz/negatiftir (anlamsız).
- Dolar şoku günlerinde ihracatçı–banka ayrışması en yüksek seviyeye çıkar.
- Günlük ölçekte dolar ile borsa arasında güçlü bir öncülük ilişkisi yoktur; ilişki
  eşzamanlı ve zayıftır (R² ≈ %1).

---

## Projeyi Çalıştırma Talimatları

### 1. Gereksinimler
- **Python 3.12** (3.10+ çalışır)
- İnternet bağlantısı (veri Yahoo Finance'ten canlı çekilir)

### 2. Kütüphanelerin Kurulumu
```bash
pip install pandas numpy matplotlib seaborn statsmodels yfinance notebook
```

### 3. Notebook'u Çalıştırma
```bash
# Proje klasöründe:
jupyter notebook analiz.ipynb
# Açılan arayüzde: Kernel > Restart & Run All (tüm hücreleri sırayla çalıştırır)
```
`jupyter` komutu PATH'te değilse: `python -m jupyter notebook analiz.ipynb`

> **Önemli:** `analiz.ipynb` **tek dosyada, kendi kendine yeten** bir çalışmadır; veri
> yükleme, temizleme, EDA ve modelleme adımlarının tamamını içerir. Ayrıca bir veri
> dosyası indirmenize gerek yoktur — notebook veriyi `yfinance` ile otomatik çeker.
> (İlk çalıştırmada veri indirme ~30–60 saniye sürebilir.)

> **Veri güncelliği hakkında:** Notebook veriyi her çalıştırmada Yahoo Finance'ten
> **canlı** çeker; bu nedenle çalıştırmak için **internet bağlantısı gereklidir**. Analiz
> dönemi 2021-07-01 – 2026-07-01 tarihlerine sabitlendiğinden sonuçlar çalıştırmadan
> çalıştırmaya büyük ölçüde aynı kalır; ancak Yahoo Finance geçmiş veride küçük düzeltmeler
> (fiyat revizyonu, temettü ayarı vb.) yapabildiği için katsayıların son basamaklarında
> önemsiz farklar görülebilir. Sonuçların bire bir sabit kalması isteniyorsa, `veri_toplama.py`
> ile bir kez çekilip `data/processed/` altına kaydedilen CSV dosyaları kullanılabilir.

### 4. Dosya Yapısı

**Çalışmak için gereken tek dosya `analiz.ipynb`'dir.** Notebook veriyi kendisi çeker;
aşağıdaki yardımcı scriptlerin hiçbiri çalışma zamanında gerekli değildir.

**Teslim edilen ana çıktılar:**
| Dosya | Açıklama |
|-------|----------|
| `analiz.ipynb` | **Ana dosya** — veri yükleme, temizleme, EDA ve modellemenin tamamı |
| `Proje_Raporu.docx` | Yazılı proje raporu (3–5 sayfa) |
| `README.md` | Bu dosya |

---

## Kullanılan Kütüphaneler

| Kütüphane | Sürüm | Kullanım | Lisans |
|-----------|-------|----------|--------|
| pandas | 3.0.2 | Veri işleme, temizleme | BSD-3-Clause |
| numpy | 2.3.5 | Sayısal hesaplama | BSD-3-Clause |
| matplotlib | 3.10.8 | Görselleştirme | PSF (matplotlib lisansı) |
| seaborn | 0.13.2 | İstatistiksel görselleştirme | BSD-3-Clause |
| statsmodels | 0.14.6 | Doğrusal regresyon (OLS) | BSD-3-Clause |
| yfinance | 1.5.1 | Veri çekme (Yahoo Finance) | Apache-2.0 |

---

## Veri Kaynağı ve Lisansı

- **Kaynak:** [Yahoo Finance](https://finance.yahoo.com) — `yfinance` Python kütüphanesi
  aracılığıyla erişilmiştir.
- **Çekilen semboller:** 12 BIST hissesi (`THYAO.IS`, `GARAN.IS`, `AKBNK.IS`, `ISCTR.IS`,
  `ASELS.IS`, `KCHOL.IS`, `SAHOL.IS`, `EREGL.IS`, `TUPRS.IS`, `BIMAS.IS`, `SISE.IS`,
  `TCELL.IS`), USD/TRY kuru (`TRY=X`) ve ons altın (`GC=F`).
- **Lisans / Kullanım koşulları:** `yfinance` kütüphanesi **Apache 2.0** lisanslıdır.
  Yahoo Finance verisinin kendisi Yahoo'nun kullanım şartlarına tabidir ve **kişisel,
  akademik ve araştırma amaçlı** kullanım içindir; ticari yeniden dağıtımı kısıtlıdır.
  Bu proje yalnızca eğitim amaçlı hazırlanmıştır.

---

### Kullanılan Modeller

- Claude Fable 5 - Proje Taslağı oluşturma ve Tasarım Kararları
- Claude Opus 4.8 - Kodlama Asistanı
- Perplexity Sonar - Hisse Seçimi

