# 📈 FinAnalyst-n8n: Otomatik Finansal Piyasalar & İnteraktif AI Portföy Analiz Motoru

<img width="1920" height="963" alt="borsatakip" src="https://github.com/user-attachments/assets/811d39db-c171-48df-8899-9eb3f7ab961d" />

<img width="1913" height="966" alt="borsatakip2" src="https://github.com/user-attachments/assets/183bc851-a1a2-4e8a-81c6-12b54f44173f" />

**FinAnalyst-n8n**, Borsa İstanbul (BIST), Kripto Para Piyasaları, Değerli Madenler / Döviz ve Son Halka Arzların (IPO) anlık ve geçmiş verilerini modüler olarak toplayan, analiz eden **günlük otomatik e-posta bülteni** ile Telegram üzerinden anlık nicel teknik analiz raporları üreten **interaktif bot motorunu** tek bir çatıda birleştiren **n8n tabanlı gelişmiş finansal istihbarat ve analiz ekosistemidir**.

---

## 🛠️ Sistem Çözümü: 2 Ana İş Akışı (Workflows)

Proje birbiriyle entegre çalışan **2 temel n8n iş akışından** oluşmaktadır:

1. 📬 **Günlük Otomatik E-Posta Bülten Akışı:** Her gün belirlenen saatte tetiklenerek BIST, Kripto, Değerli Madenler, Halka Arzlar ve AI Makro özetini senkronize edip mobil uyumlu HTML mail olarak gönderir.
2. 🤖 **İnteraktif Telegram Komut Motoru (`/analiz`):** Telegram üzerinden gelen canlı komutları (`/analiz THYAO`, `/analiz BTC` vb.) dinler; 1 yıllık borsa verilerini, hareketli ortalamaları (SMA) ve hacim dinamiklerini Llama 3.3 (70B) AI modeliyle sentezleyip anlık nicel rapor üretir.

---

## 📌 Öne Çıkan Özellikler

### 1. 🤖 İnteraktif Telegram Analiz Botu (`/analiz`)
- 💬 **Anlık Komut Algılama:** Telegram üzerinden gönderilen `/analiz <SEMBOL>` komutlarını anında işleme alma.
- 📊 **1 Yıllık Multi-Timeframe Veri Seti:** Yahoo Finance API üzerinden son 365 günün fiyat, kapanış ve hacim verilerini çekme.
- 📐 **Otomatik Nicel (Quant) İndikatör Hesaplama:**
  - **Kısa / Orta / Uzun Vadeli Ortalamalar:** SMA 20, SMA 50 ve SMA 200 değerlerinin anlık hesaplanması.
  - **Hacim Momentum Analizi:** Son günkü işlem hacmi ile 30 günlük ortalama hacmin kıyaslanması (Para girişi/çıkışı tespiti).
  - **Mikro & Makro Trend:** Son 15 günün günlük kapanışları ile 52 haftalık dip/tepe seviyelerinin tespiti.
- 🧠 **Llama 3.3 70B AI Strateji Motoru:** Groq API altyapısıyla verileri işleyip Telegram HTML formatında destek/direnç, trend yönü ve net tavsiye kararı (`🟢 GÜÇLÜ AL`, `🟢 DİP ALIMI`, `🟡 NÖTR-BEKLE`, `🔴 SAT`) üretme.
- ⚡ **Token & Kota Optimizasyonu:** Zengin teknik verileri ~1.000 token boyutunda işleyerek yüksek hız ve düşük API kota tüketimi sağlama.

### 2. 📈 BIST Hisse Portföy Takibi
- Takip edilen hisse senetleri (`KCHOL`, `ASELS`, `TUPRS`, `SAHOL`, `FROTO`, `PGSUS`, `THYAO`, `EREGL`, `ASTOR`) için **Günlük (%10 BIST tavan/taban devre kesici törpülü)**, **Haftalık (5 iş günü)**, **Aylık**, **3 Aylık** ve **Yıllık** getiri hesaplamaları.
- Yahoo Finance API entegrasyonu.

### 3. 🪙 Kripto Para Piyasası (Binance API)
- Major ve altcoinler (`BTC`, `ETH`, `SOL`, `XRP`, `MMT`, `EIGEN`) için Binance Klines (Mum verileri) API'si üzerinden **Günlük, Haftalık, Aylık, 3 Aylık ve Yıllık** performans analizi.

### 4. 🏆 Değerli Madenler & Döviz (Ons & Gram Dönüştürücü)
- Ons Altın ($) ve Ons Gümüş ($) verilerinin yanı sıra canlı Dolar/TL kuru üzerinden $1\text{ Ons} = 31.1034768\text{ Gram}$ uluslararası formülüyle **Gram Altın (TL)** ve **Gram Gümüş (TL)** fiyatlarının tarihsel tespiti ve getiri oranları.

### 5. 🚀 Akıllı Halka Arz (IPO) Takibi
- `halkarz.com` üzerinden en son işlem görmeye başlayan 5 halka arz şirketinin web scraping (kazıma) ile tespiti.
- Şirket detay sayfalarından **Orijinal Halka Arz Fiyatının (Arz Fiyatı)** çekilmesi ve borsadaki 1. günden itibaren **Gerçek Toplam Getirinin** hesaplanması.

### 6. 📧 Senkronize & Güvenli HTML Mail Bülteni
- Tüm paralel veri kollarının `Merge` düğümü ile senkronize edilerek **tek bir mail gönderimi** garantisi.
- Mobil uyumlu, renk kodlu (Kâr: Yeşil / Zarar: Kırmızı) HTML tablo tasarımı.
- Türkçe karakter encoding (`ç`, `ğ`, `ı`, `ö`, `ş`, `ü`) hatalarını önleyen özel HTML entity temizleyicisi.
- `try-catch` zırhı ile eksik düğüm/veri durumunda çökmeden çalışan dirençli kod yapısı.

---

## 📐 Sistem Mimarisi (Workflow Architecture)

### 📬 1. İş Akışı: Günlük Otomatik E-Posta Bülteni
```text
                        ┌──> [ BIST Liste ] ────────> [ BIST Yahoo Fetch ] ────────> [ BIST Hesaplayıcı ] ────────┐
                        │                                                                                         │
                        ├──> [ Kripto Liste ] ──────> [ Kripto Binance Fetch ] ────> [ Kripto Hesaplayıcı ] ────┤
                        │                                                                                         │
[ Schedule Trigger ] ───┼──> [ Maden Liste ] ───────> [ Maden Yahoo Fetch ] ───────> [ Maden Hesaplayıcı ] ─────┼──> [ Merge ] ──> [ Mail Hazırlayıcı ] ──> [ Gmail ]
                        │                                                                                         │
                        ├──> [ Yapay Zeka Analizi (Groq API) ] ─────────────────────────────────────────────────┤
                        │                                                                                         │
                        └──> [ Halka Arz Scraping ] ─> [ IPO Detay Fetch ] ────────> [ IPO Hesaplayıcı ] ───────┘
