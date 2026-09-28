# DahiliyeAsistan — Proje Talimatı (Claude / Codex)

Bu çalışma alanı, SDÜ Bilgisayar Mühendisliği bitirme projesi **DahiliyeAsistan** içindir.
Bu dosyayı her oturumun başında oku ve aşağıdaki kurallara uy.

## Proje özeti

Dahiliye stajındaki intörn hekimler için Türkçe, kaynak gösteren bir yapay zekâ asistanı.
İntörn soru sorar; sistem Türk uzmanlık derneklerinin klinik kılavuzlarına dayanarak cevap verir
ve kılavuz / bölüm / sayfa bilgisini gösterir.

Temel araştırma hedefi: dahiliye soru-cevap görevinde yeterli başarımı sağlayan **en düşük
parametre sayılı** açık kaynak dil modelini bulmak, fine-tune etmek ve kılavuz tabanlı RAG ile
birleştirmek. Ayrıntılar:

- Araştırma soruları: `docs/01-arastirma-sorulari.md`
- Model seçim ölçütleri ve aday listesi: `docs/02-model-secim-kriterleri.md`
- Doğrulama kaydı: `docs/03-kaynak-dogrulama-kaydi.md`
- Tasarım belgesi: `docs/DahiliyeAsistan_Proje_Tanim_ve_Tasarim_Belgesi.docx`
- Danışman gereksinimleri: `docs/Tasarim_Proje_Gereksinimleri.docx`

## Kaynak ve doğruluk kuralları (en önemli bölüm)

1. Bilgileri **doğrulanmış kaynak göstererek** ver. Uydurma kaynak, makale, veri seti, model adı,
   parametre sayısı, lisans veya benchmark sonucu **sunma**.
2. Her iddia için bağlantı (URL) ya da DOI ver. Model önerirken Hugging Face sayfasını ve lisansını
   yaz. Veri seti önerirken satır sayısını, lisansını ve erişim koşulunu (gated mi?) kaynak
   sayfasından aktar.
3. Bir bilgiyi kaynak sayfasında göremediysen **"DOĞRULANMADI"** diye işaretle. Tahmin ile bilgiyi
   karıştırma; tahminse "tahmin" yaz.
4. Hatırladığın bilgi ile web'de bulduğun bilgiyi ayır. Bilgi tarihliyse (sürüm, tarih, lisans)
   mutlaka güncel sayfadan kontrol et.
5. Sayı uydurma. Bilinmeyen bir değer için "bilinmiyor" yaz ve nasıl ölçülebileceğini öner.

## Araştırma çıktılarının biçimi

- Her araştırma sonucu `arastirma/` klasörüne `YYYY-AA-GG-konu.md` adıyla kaydedilir.
- Dosyanın başında: soru, tarih, kullanılan araç (Claude / Codex).
- Karşılaştırmalar tablo olarak verilir; her satırda kaynak bağlantısı bulunur.
- Dosyanın sonunda **"Doğrulanması gerekenler"** listesi olur. Öğrenci bunları elle kontrol edip
  `docs/03-kaynak-dogrulama-kaydi.md` dosyasına işler. Kontrol edilmemiş bilgi rapora girmez.

## Teknik kararlar (değiştirme, önerin varsa gerekçesiyle sor)

| Katman | Teknoloji |
|---|---|
| Fine-tuning | Google Colab + Unsloth (LoRA / QLoRA) → GGUF |
| Model servisi | Ollama (LLM + embedding) |
| Vektör veritabanı | Qdrant |
| Backend | Python, FastAPI |
| Veritabanı | PostgreSQL |
| Web | React (Vite) |
| Mobil | React Native (Expo), gerçek cihaz |
| Kurulum | docker-compose (Windows: Docker Desktop + WSL2) |
| Kılavuz işleme | Python (PyMuPDF metin, pdfplumber tablo) |

## Kod kuralları

- Öğrenci Python'a yeni başlıyor (MERN geçmişi var). Python kodunda kısa Türkçe açıklama satırları
  kullan; gerektiğinde Express karşılığını belirt.
- Parçalama, embedding ve istem (prompt) oluşturma kodu **tek yerde** yazılır ve hem `ingest/`,
  hem `backend/`, hem `eval/` tarafından ortak kullanılır.
- Dizin oluşturma ve sorgu aşamalarında **aynı embedding modeli** kullanılır.
- Gizli bilgiler (token, şifre) `.env` dosyasında tutulur, koda yazılmaz.
- Kılavuz PDF'leri ve veri setleri `data/` altında durur ve Git'e eklenmez (lisans gereği).

## Klasör yapısı

```
docs/        Proje belgeleri, araştırma soruları, model kriterleri, doğrulama kaydı
arastirma/   Yapay zekâ araçlarıyla yapılan araştırmaların çıktıları (tarihli .md)
notebooks/   Colab notebook'ları (veri ayıklama, fine-tuning, model tarama)
data/        Ham ve işlenmiş veri (Git'e girmez)
ingest/      Kılavuz PDF işleme hattı (Python)
backend/     FastAPI servisi
eval/        Değerlendirme betikleri
web/         React (Vite) uygulaması
mobile/      React Native (Expo) uygulaması
```
