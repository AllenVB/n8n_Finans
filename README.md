# 🤖 BIST & Crypto AI Daily Analyst (n8n Workflow)

Bu proje, her sabah Borsa İstanbul hisselerini ve kripto para verilerini otomatik olarak çekip, **Llama 3.3 (Groq API)** yardımıyla derinlemesine teknik analizler üreten ve bunları kullanıcıya şık bir e-posta bülteni olarak gönderen tam otomatik bir **n8n** akışıdır.

<img width="1665" height="879" alt="image" src="https://github.com/user-attachments/assets/8eeae7cb-dbf6-4ff0-b147-bc5bd1bf8337" />


## 🚀 Özellikler
- 🕒 **Otomatik Zamanlayıcı (Schedule):** Her sabah belirlenen saatte (Örn: 09:00 TR) otomatik tetiklenme.
- 📈 **Canlı Finans Verisi:** Yahoo Finance ve Binance API'leri üzerinden canlı veri entegrasyonu (KCHOL, TUPRS, SAHOL, ASELSAN, AYGZ, Kripto ve döviz çiftleri).
- 🧠 **Teknik Analiz Motoru (AI):** Llama 3.3 modeliyle haftalık/aylık kâr-zarar trendlerini analiz eder, destek ve direnç seviyelerine yakınlığa göre akümülasyon veya kâr realizasyonu önerileri sunar.
- 📧 **Kusursuz HTML E-posta:** Türkçe karakter problemi (HTML Entity kodlamasıyla) tamamen çözülmüş, göz yormayan minimalist Arial tasarım ve durum emojileriyle (🔴/🟢) donatılmış HTML bülten şablonu.

## 🛠️ Kullanılan Teknolojiler
- **n8n Cloud** (Workflow Automation)
- **Groq API / Llama 3.3-70b-versatile** (LLM & Technical Analysis)
- **JavaScript (ES6)** (Data Transformation & HTML Generation)
- **Yahoo Finance API & Binance API** (Financial Data Source)

## 📦 Kurulum ve Kullanım
1. Bu depodaki `workflow.json` dosyasını bilgisayarınıza indirin.
2. Kendi n8n hesabınıza giriş yapın.
3. Yeni bir workflow oluşturup sağ üst menüden **Import from File** seçeneği ile bu JSON dosyasını içeri aktarın.
4. `Yapay Zeka Analizi` düğümüne tıklayarak kendi **Groq API Key** bilginizi tanımlayın.
5. `Send an Email` düğümünde kendi **SMTP/E-posta** bilgilerinizi yapılandırın.
6. Sağ üstten **Publish** (veya Save) butonuna basarak akışı aktif hale getirin.
