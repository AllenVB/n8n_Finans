# 📈 FinAnalyst-n8n: Otomatik Finansal Piyasalar & İnteraktif AI Portföy Analiz Motoru

--FİNANSÖR--
Bu yapı günlük olarak piyasalarda takip ettiğim varlıkları her sabah bana güncel değişimlerini iletiyor.
<img width="1920" height="1006" alt="Finansör" src="https://github.com/user-attachments/assets/aea993a7-9db4-4dcc-8d2a-f2d401e49705" />
--GÜNLÜK FİNANS GELİŞMELERİ HER SABAH 10.15'DE YAPAY ZEKA YOLUYLA YORUMLANARAK MESAJ BİLDİRİYOR--
<img width="1690" height="840" alt="mail1" src="https://github.com/user-attachments/assets/b717416e-088a-4f49-9dfb-54651996f53c" />
<img width="1701" height="899" alt="mail2" src="https://github.com/user-attachments/assets/8ba4db65-7eb7-4e09-a150-443fba2cc259" />

<------------------------------------------------------------------------------------------------------------------------->

--VERİ MADENCİSİ--
Bu robot telegram kanalındaki verileri kendi kanalımıza aktarıyor
<img width="1920" height="999" alt="veri madencisi" src="https://github.com/user-attachments/assets/534302c2-478e-4647-895f-72ee591c99d2" />
--TELEGRAM KOMUT ROBOTU--
Bu robot telegramdaki kendi kanalımıza aktarılan verileri  çekmemize yardımcı oluyor.
<img width="1920" height="999" alt="telegram komut" src="https://github.com/user-attachments/assets/61ff1c07-a789-484f-8c31-e4fdab54d9a6" />
--YAPAY ZEKA BOTU ANALİZ RAPORU--
<img width="1457" height="835" alt="analiz" src="https://github.com/user-attachments/assets/68390dba-92e8-459b-9164-1637726fae6c" />

--SHEETS TABLOLARI -- TELEGRAM ANALIZ KANALINDAN GELEN VERİLER SONUCU--
Veriler tablolanarak kayıt ediliyor.
<img width="1920" height="997" alt="sheets2" src="https://github.com/user-attachments/assets/b53a10e3-aaa7-47f8-ba25-9e409a848186" />
<img width="1920" height="972" alt="sheets1" src="https://github.com/user-attachments/assets/9ccd7494-f166-4171-82a4-d046616f15e4" />


**FinAnalyst-n8n**, Borsa İstanbul (BIST), Kripto Para Piyasaları, Değerli Madenler / Döviz ve Son Halka Arzların (IPO) anlık ve geçmiş verilerini modüler olarak toplayan, analiz eden **günlük otomatik e-posta bülteni**, Telegram üzerinden anlık nicel teknik analiz raporları üreten **interaktif bot motoru** ve Telegram kanallarından gelen ham akışları yapay zeka ile filtreleyerek yapılandıran **Veri Madencisi (Data Miner)** modüllerini tek bir çatıda birleştiren **n8n tabanlı gelişmiş finansal istihbarat ve analiz ekosistemidir**.

---

## 🛠️ Sistem Çözümü: Temel İş Akışları (Workflows)

Proje birbiriyle entegre çalışan temel n8n iş akışlarından oluşmaktadır:

1. 📬 **Günlük Otomatik E-Posta Bülten Akışı:** Her gün belirlenen saatte tetiklenerek BIST, Kripto, Değerli Madenler, Halka Arzlar ve AI Makro özetini senkronize edip mobil uyumlu HTML mail olarak gönderir.
2. 🤖 **İnteraktif Telegram Komut Motoru (`/analiz`):** Telegram üzerinden gelen canlı komutları dinler; 1 yıllık borsa verilerini, hareketli ortalamaları (SMA) ve hacim dinamiklerini AI modeliyle sentezleyip anlık nicel rapor üretir.
3. ⛏️ **Telegram Veri Madencisi & Akıllı Filtreleme Motoru:** Telegram sinyal/analiz kanallarından gelen mesajları anlık dinleyen, Groq LLM (Llama 3.1/3.3) desteğiyle gürültüyü (sohbet, sitem, reklam, ham makro haberler) ve gerçek teknik/temel analizleri ayırt eden; analizleri **Ana Tabloya**, gürültüleri ise **Log Tablosuna** otomatik kategorize ederek işleyen otonom yapı.

---

## 📌 Öne Çıkan Özellikler

### 1. ⛏️ Telegram Kanalı Otomatik Veri Madencisi & NLP Filtreleme
- 🔍 **Akıllı Gürültü Filtreleme (Noise Reduction):** Telegram gruplarından/kanallarından gelen mesajları yapay zeka süzgecinden geçirerek sıradan sohbetleri, isyanları, reklamları ve yönsüz makro haberleri `GÜRÜLTÜ` olarak ayırır.
- 🎯 **Ticker & Sembol Önceliklendirme:** Mesaj içerisinde BIST hisse kodları (`THYAO`, `ASELS`, `YKBNK` vb.) veya kripto para birimleri (`BTC`, `ETH`, `EIGEN` vb.) geçtiğinde, mesajda rakamsal fiyat olmasa bile (örn. "destekte, direnç potansiyeli var") bunu yakalayıp yapılandırılmış bir analize dönüştürür.
- 📊 **Çift Katmanlı Google Sheets Entegrasyonu:** 
  - **Ana Tablo (`AI_Borsa_Sinyalleri`):** Varlık, Sinyal Yönü (AL/SAT/TUT/NOTR), Genel Duygu, Hedefler, Stop-Loss ve Temel Gerekçe sütunlarıyla temiz sinyal veritabanı.
  - **Log Tablosu (`Loglar`):** Filtrelenen tüm ham mesajların zaman damgasıyla arşivlendiği denetim katmanı.

### 2. 🤖 İnteraktif Telegram Analiz Botu (`/analiz`)
- 💬 **Anlık Komut Algılama:** Telegram üzerinden gönderilen `/analiz <SEMBOL>` komutlarını anında işleme alma.
- 📊 **1 Yıllık Multi-Timeframe Veri Seti:** Yahoo Finance API üzerinden son 365 günün fiyat, kapanış ve hacim verilerini çekme.
- 📐 **Otomatik Nicel (Quant) İndikatör Hesaplama:**
  - **Kısa / Orta / Uzun Vadeli Ortalamalar:** SMA 20, SMA 50 ve SMA 200 değerlerinin anlık hesaplanması.
  - **Hacim Momentum Analizi:** Son günkü işlem hacmi ile 30 günlük ortalama hacmin kıyaslanması (Para girişi/çıkışı tespiti).
  - **Mikro & Makro Trend:** Son 15 günün günlük kapanışları ile 52 haftalık dip/tepe seviyelerinin tespiti.
- 🧠 **AI Strateji Motoru:** Groq API altyapısıyla verileri işleyip Telegram HTML formatında destek/direnç, trend yönü ve net tavsiye kararı üretme.
- ⚡ **Token & Kota Optimizasyonu:** Zengin teknik verileri optimize ederek yüksek hız ve düşük API kota tüketimi sağlama.

### 3. 📈 BIST Hisse Portföy Takibi
- Takip edilen hisse senetleri (`KCHOL`, `ASELS`, `TUPRS`, `SAHOL`, `FROTO`, `PGSUS`, `THYAO`, `EREGL`, `ASTOR`) için **Günlük**, **Haftalık (5 iş günü)**, **Aylık**, **3 Aylık** ve **Yıllık** getiri hesaplamaları.
- Yahoo Finance API entegrasyonu.

### 4. 🪙 Kripto Para Piyasası (Binance API)
- Major ve altcoinler (`BTC`, `ETH`, `SOL`, `XRP`, `MMT`, `EIGEN`) için Binance Klines (Mum verileri) API'si üzerinden performans analizi.

### 5. 🏆 Değerli Madenler & Döviz (Ons & Gram Dönüştürücü)
- Ons Altın ($) ve Ons Gümüş ($) verilerinin yanı sıra canlı Dolar/TL kuru üzerinden 1 Ons = 31.1034768 Gram uluslararası formülüyle **Gram Altın (TL)** ve **Gram Gümüş (TL)** fiyatlarının tarihsel tespiti ve getiri oranları.

### 6. 🚀 Akıllı Halka Arz (IPO) Takibi
- `halkarz.com` üzerinden en son işlem görmeye başlayan halka arz şirketlerinin web scraping ile tespiti ve borsadaki 1. günden itibaren **Gerçek Toplam Getirinin** hesaplanması.

### 7. 📧 Senkronize & Güvenli HTML Mail Bülteni
- Tüm paralel veri kollarının `Merge` düğümü ile senkronize edilerek **tek bir mail gönderimi** garantisi.
- Mobil uyumlu, renk kodlu (Kâr: Yeşil / Zarar: Kırmızı) HTML tablo tasarımı.
- Türkçe karakter encoding hatalarını önleyen özel temizleyici yapı.

---

## 📐 Sistem Mimarisi (Workflow Architecture)

### 📬 1. İş Akışı: Günlük Otomatik E-Posta Bülteni
```text
                       ┌──> [ BIST Liste ] ────────> [ BIST Yahoo Fetch ] ────────> [ BIST Hesaplayıcı ] ────────┐
                       │                                                                                        │
                       ├──> [ Kripto Liste ] ──────> [ Kripto Binance Fetch ] ────> [ Kripto Hesaplayıcı ] ────┤
                       │                                                                                        │
[ Schedule Trigger ] ───┼──> [ Maden Liste ] ───────> [ Maden Yahoo Fetch ] ───────> [ Maden Hesaplayıcı ] ─────┼──> [ Merge ] ──> [ Mail Hazırlayıcı ] ──> [ Gmail ]
                       │                                                                                        │
                       ├──> [ Yapay Zeka Analizi (Groq API) ] ─────────────────────────────────────────────────┤
                       │                                                                                        │
                       └──> [ Halka Arz Scraping ] ─> [ IPO Detay Fetch ] ────────> [ IPO Hesaplayıcı ] ───────┘
