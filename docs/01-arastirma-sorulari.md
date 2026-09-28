# Araştırma Soruları

Projenin deneysel bölümü aşağıdaki beş soruya cevap arar. Her deney, en az bir soruya hizmet etmelidir.

| Kod | Konu | Soru | Nasıl ölçülecek |
|---|---|---|---|
| AS1 | Ölçek | Dahiliye soru-cevap görevinde kabul edilebilir başarımı sağlayan **en düşük parametre sayılı** model hangisidir? Parametre sayısı ile başarım arasındaki ilişki nasıl bir eğri izler? | Aday modeller fine-tune öncesi aynı test verisinde taranır; parametre–doğruluk eğrisi çizilir |
| AS2 | Fine-tuning katkısı | Seçilen modelin dahiliye verisiyle fine-tune edilmesi, temel modele göre anlamlı bir başarım artışı sağlar mı? | S0 (temel) ile S3 (FT-Dahiliye) karşılaştırması |
| AS3 | Alan daraltma | Yalnızca dahiliye alt kümesiyle eğitim, veri setinin tamamıyla yapılan genel eğitimden daha mı başarılıdır? | S2 (FT-Genel) ile S3 (FT-Dahiliye) karşılaştırması |
| AS4 | RAG katkısı | Kılavuz tabanlı RAG, fine-tune edilmiş modele ek katkı sağlar mı? Hatalar arama aşamasından mı, üretim aşamasından mı kaynaklanır? | S3 ile S4 karşılaştırması; Recall@k (arama) ve okuma doğruluğu (üretim) ayrı ölçülür |
| AS5 | Dış karşılaştırma | Küçük model + fine-tuning + RAG, 9B parametreli TUSGPT modelinin dahiliye başarımına hangi donanım maliyetiyle yaklaşabilir? | S4 ile S5 (TUSGPT-TR-Medical-9B); doğruluk, bellek, cevap süresi |

## Karşılaştırılacak sistemler

| Kod | Sistem |
|---|---|
| S0 | Temel model (fine-tuning öncesi) |
| S1 | Temel model + RAG |
| S2 | FT-Genel (TUSGPT verisinin tamamı) |
| S3 | FT-Dahiliye |
| S4 | FT-Dahiliye + RAG (önerilen sistem) |
| S5 | TUSGPT-TR-Medical-9B |
| S6 | Ticari büyük dil modeli (üst sınır referansı) |

## Açık sorular (danışmanla netleşecek)

- "Kabul edilebilir başarım" eşiği: en iyi adaya göre en fazla **3 puan** fark önerildi.
- Proje test setinin büyüklüğü (100–150 soru önerildi) ve kimin kontrol edeceği.
