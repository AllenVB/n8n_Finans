🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀--FİNANSÖR--🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀

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
Bu robot telegramdaki kendi kanalımıza aktarılan verileri  çekmemize yardımcı oluyor.
<img width="1920" height="999" alt="telegram komut" src="https://github.com/user-attachments/assets/61ff1c07-a789-484f-8c31-e4fdab54d9a6" />
--YAPAY ZEKA BOTU ANALİZ RAPORU--
<img width="1457" height="835" alt="analiz" src="https://github.com/user-attachments/assets/68390dba-92e8-459b-9164-1637726fae6c" />

--SHEETS TABLOLARI -- TELEGRAM ANALIZ KANALINDAN GELEN VERİLER SONUCU--
Veriler tablolanarak kayıt ediliyor.
<img width="1920" height="997" alt="sheets2" src="https://github.com/user-attachments/assets/b53a10e3-aaa7-47f8-ba25-9e409a848186" />
<img width="1920" height="972" alt="sheets1" src="https://github.com/user-attachments/assets/9ccd7494-f166-4171-82a4-d046616f15e4" />

🎯🎯🎯🎯YATIRIM TAVSİYE SİSTEMİ🎯🎯🎯🎯

Veriler sosyal medyadaki önemli borsa yatırımcıları tarafından edilen analizler sonucunda toplanıyor.Videolar mp4 halinden text'e dönüştürülüp , tavsiyelerin sonuçları kaydediliyor.
<img width="1920" height="1001" alt="Apify-Scraping" src="https://github.com/user-attachments/assets/e093dab6-04a6-455a-8bc1-de43c10cd653" />
Ardından toplanan veriler en küçük yapıya kadar işleniyor. (İsim , Şu Anki Fiyat , Hedef Fiyat , Stop , Yorum) şeklinde.
<img width="1920" height="967" alt="ekoanaliz" src="https://github.com/user-attachments/assets/e4ce57b5-7bd2-496d-8847-2a87953caa7a" />
En sade hali ile her sabah maile yatırım tavsiyeleri iletiliyor.
<img width="1650" height="798" alt="mailrapor" src="https://github.com/user-attachments/assets/ac0f2565-7eac-4a27-bb03-6ad26d90654e" />


<------------------------------------------------------------------------------------------------------------------------------------->


## 🚀 Proje Mimarisi ve Sistem Özeti

Bu proje, finansal piyasaları (BİST, Kripto, Değerli Madenler, Halka Arzlar) 7/24 izleyen, farklı kaynaklardan veri toplayan ve yapay zeka (LLM) destekli analizler sunan tam otomatik bir **Nicel Piyasa Analiz ve Portföy Yönetim Ekosistemidir**. 

Sistem, `n8n` orkestrasyon aracı üzerinde çalışan ve birbirini tamamlayan 4 ana iş akışından (workflow) oluşmaktadır.

### 1. Apify Web Scraping & AI Sinyal Botu
Sosyal medya üzerindeki finansal analizleri ve sinyalleri otomatik olarak yakalayıp yapılandıran iş akışıdır.
* **Veri Toplama:** Zamanlayıcı tetiklemesiyle çalışır ve Apify "X Tweet Scraper" aktörünü kullanarak X (Twitter) üzerinden veri kazır[cite: 1].
* **Medya İşleme:** Tespit edilen videolu içerikler indirilir ve Groq API (Whisper-large-v3-turbo) kullanılarak sesten metne dönüştürülür[cite: 1].
* **Yapay Zeka Analizi:** Çekilen metinler Llama-3.1-8b-instant modeliyle analiz edilir[cite: 1]. Metin içerisindeki varlık adı, anlık fiyat, hedef fiyat, stop seviyesi ve genel yorum ayrıştırılarak JSON formatına çevrilir[cite: 1].
* **Kayıt ve Bildirim:** Geçerli veriler Google Sheets tablosuna kaydedilir ve son 10 kaydın yer aldığı bir özet e-posta (HTML formatında) olarak kullanıcıya gönderilir[cite: 1].

### 2. İnteraktif Telegram Komut Motoru
Kullanıcıların anlık olarak istedikleri bir varlık (Hisse veya Kripto) hakkında detaylı analiz alabilmesini sağlayan interaktif bottur.
* **Tetikleyici:** Telegram üzerinden gönderilen `/analiz THYAO` veya `/analiz BTC` gibi komutlarla tetiklenir[cite: 2].
* **Teknik Veri Entegrasyonu:** İstenen varlığın hareketli ortalamaları (SMA20, SMA50, SMA200) ve hacim verileri Yahoo Finance API üzerinden çekilir[cite: 2].
* **Hissiyat Analizi:** TradingView RSS beslemesi üzerinden ilgili varlığa ait güncel analist fikirleri toplanır[cite: 2].
* **Nicel Raporlama:** Yapay zeka modeli (Llama-3.3-70b-versatile); teknik verileri ve analist fikirlerini sentezleyerek "Güçlü Al / Sat / Nötr" sinyallerini içeren kapsamlı bir HTML Telegram mesajı oluşturur ve kullanıcıya iletir[cite: 2].

### 3. Kapsamlı Borsa ve Portföy Takip Sistemi
Piyasadaki tüm makro ve mikro verileri harmanlayarak günlük strateji raporu üreten ana motor.
* **Zamanlanmış Çalışma:** Her gün saat 10:15 ve 13:00'te otomatik olarak çalışır[cite: 3].
* **Çoklu Veri Akışı:** Halkarz.com üzerinden yeni halka arz verilerini[cite: 3], Yahoo Finance üzerinden BİST ve değerli maden/döviz (Altın, Gümüş, USD/TRY) verilerini[cite: 3], Binance API üzerinden ise kripto para verilerini toplar[cite: 3].
* **Performans Ölçümü:** Toplanan veriler işlenerek varlıkların günlük, haftalık, aylık, 3 aylık ve yıllık yüzde (%) değişim oranları hesaplanır[cite: 3].
* **Haber ve AI Sentezi:** Google News RSS üzerinden piyasa haberleri çekilir[cite: 3]. Tüm sayısal veriler ve haberler bir araya getirilerek Llama modeline sunulur; aşırı satım uyarıları, değer tuzakları ve yön tahminleri içeren detaylı bir strateji raporu oluşturulur[cite: 3]. Bu rapor e-posta ve Telegram üzerinden iletilir[cite: 3].

### 4. Telegram Veri Madencisi ve NLP Filtresi
Telegram kanallarından veya gruplarından gelen düz metinleri filtreleyip sinyale dönüştüren dil işleme akışıdır.
* **Metin Sınıflandırma:** Telegram'a düşen mesajları yakalar ve LLM (Llama-3.1-8b) kullanarak mesajın bir "ANALİZ" (sinyal) mi yoksa "GÜRÜLTÜ" (sıradan sohbet/haber) mü olduğunu tespit eder[cite: 4].
* **Veri Ayrıştırma:** "ANALİZ" olarak işaretlenen mesajlardan varlık adı, sinyal yönü (Al/Sat/Tut), giriş seviyesi, hedefler, stop-loss, vade ve duygu (sentiment) bilgileri çıkarılır[cite: 4].
* **Veritabanı Yönetimi:** Geçerli finansal analizler ana Google Sheets tablosuna yazılırken, analiz niteliği taşımayan "Gürültü" mesajlar ayrı bir Log tablosuna kaydedilir[cite: 4].

---

## 🛠️ Kullanılan Teknolojiler (Tech Stack)

* **Orkestrasyon:** n8n (Node tabanlı otomasyon)
* **Yapay Zeka (LLM & Audio):** Groq API (Llama 3.1 8B, Llama 3.3 70B, Whisper-large-v3-turbo)
* **Veri Kazıma (Web Scraping):** Apify (X Tweet Scraper)
* **Finansal API'ler:** Yahoo Finance API, Binance API
* **Haber & Veri Kaynakları:** Google News RSS, TradingView RSS, Halkarz.com
* **Veritabanı & Bildirim:** Google Workspace (Sheets, Gmail), Telegram Bot API

## ⚙️ Kurulum ve Dağıtım (Setup)

1. Depoda bulunan `.json` uzantılı iş akışı (workflow) dosyalarını n8n paneline import edin.
2. Sistemin çalışabilmesi için n8n üzerinde şu kimlik bilgilerini (credentials) tanımlayın:
   * `Telegram API`
   * `Groq API`
   * `Apify OAuth2 API`
   * `Google Sheets OAuth2 API`
   * `Gmail OAuth2 API / SMTP`
3. Dosyaların içindeki e-posta adreslerini, Google Sheets ID'lerini ve Telegram Chat ID'lerini kendi bilgilerinize göre güncelleyin.
4. Akışları aktifleştirin (Activate) ve Schedule (Zamanlayıcı) düğümlerinin saat dilimlerinin doğru ayarlandığından emin olun.
