# 📈 FinAnalyst-n8n: Otomatik Finansal Piyasalar & Portföy Raporlama Sistemi

<img width="1920" height="1007" alt="borsatakip2" src="https://github.com/user-attachments/assets/7ed39d1c-4f1d-493a-ab3c-d0ec328b8880" /> 
<img width="1738" height="922" alt="borsatakip" src="https://github.com/user-attachments/assets/4834708a-ff09-4d70-a7d4-b3f2e0e53a9c" />

![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

**FinAnalyst-n8n**, Borsa İstanbul (BIST), Kripto Para Piyasaları, Değerli Madenler / Döviz ve Son Halka Arzların (IPO) anlık ve geçmiş verilerini modüler olarak toplayan, analiz eden ve günlük olarak tek bir senkronize e-posta bülteni halinde sunan **n8n tabanlı otomatik bir finansal istihbarat iş akışıdır (workflow)**.

---

## 📌 Öne Çıkan Özellikler

- 📈 **BIST Hisse Portföy Takibi:**
  - Takip edilen hisse senetleri (`KCHOL`, `ASELS`, `TUPRS`, `SAHOL`, `FROTO`, `PGSUS`, `THYAO`, `EREGL`, `ASTOR`) için **Günlük (%10 BIST tavan/taban devre kesici törpülü)**, **Haftalık (5 iş günü)**, **Aylık**, **3 Aylık** ve **Yıllık** getiri hesaplamaları.
  - Yahoo Finance API entegrasyonu.
- 🪙 **Kripto Para Piyasası (Binance API):**
  - Major ve altcoinler (`BTC`, `ETH`, `SOL`, `XRP`, `MMT`, `EIGEN`) için Binance Klines (Mum verileri) API'si üzerinden **Günlük, Haftalık, Aylık, 3 Aylık ve Yıllık** performans analizi.
- 🏆 **Değerli Madenler & Döviz (Ons & Gram Dönüştürücü):**
  - Ons Altın ($) ve Ons Gümüş ($) verilerinin yanı sıra canlı Dolar/TL kuru üzerinden $1\text{ Ons} = 31.1034768\text{ Gram}$ uluslararası formülüyle **Gram Altın (TL)** ve **Gram Gümüş (TL)** fiyatlarının tarihsel tespiti ve getiri oranları.
- 🚀 **Akıllı Halka Arz (IPO) Takibi:**
  - `halkarz.com` üzerinden en son işlem görmeye başlayan 5 halka arz şirketinin web scraping (kazıma) ile tespiti.
  - Şirket detay sayfalarından **Orijinal Halka Arz Fiyatının (Arz Fiyatı)** çekilmesi ve borsadaki 1. günden itibaren **Gerçek Toplam Getirinin** hesaplanması.
- 🤖 **Yapay Zeka Destekli Teknik Analiz Raporu:**
  - Groq / LLM API entegrasyonu ile piyasa verilerine dayalı günlük teknik özet ve analiz notları.
- 📧 **Senkronize & Güvenli HTML Mail Bülteni:**
  - Tüm paralel veri kollarının `Merge` düğümü ile senkronize edilerek **tek bir mail gönderimi** garantisi.
  - Mobil uyumlu, renk kodlu (Kâr: Yeşil / Zarar: Kırmızı) HTML tablo tasarımı.
  - Türkçe karakter encoding (`ç`, `ğ`, `ı`, `ö`, `ş`, `ü`) hatalarını önleyen özel HTML entity temizleyicisi.
  - `try-catch` zırhı ile eksik düğüm/veri durumunda çökmeden çalışan dirençli kod yapısı.

---

## 📐 Sistem Mimarisi (Workflow Architecture)

```text
                        ┌──> [ BIST Liste ] ────────> [ BIST Yahoo Fetch ] ────────> [ BIST Hesaplayıcı ] ────────┐
                        │                                                                                       │
                        ├──> [ Kripto Liste ] ──────> [ Kripto Binance Fetch ] ────> [ Kripto Hesaplayıcı ] ────┤
                        │                                                                                       │
[ Schedule Trigger ] ───┼──> [ Maden Liste ] ───────> [ Maden Yahoo Fetch ] ───────> [ Maden Hesaplayıcı ] ─────┼──> [ Merge ] ──> [ Mail Hazırlayıcı ] ──> [ Gmail ]
                        │                                                                                       │
                        ├──> [ Yapay Zeka Analizi (Groq API) ] ─────────────────────────────────────────────────┤
                        │                                                                                       │
                        └──> [ Halka Arz Scraping ] ─> [ IPO Detay Fetch ] ────────> [ IPO Hesaplayıcı ] ───────┘
