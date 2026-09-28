# İlk Araştırma Görevleri (kopyala, yapıştır)

Aşağıdaki istemleri Claude veya Codex'e sırayla ver. Her biri `AGENTS.md` kurallarına göre çalışır ve
çıktısını `arastirma/` klasörüne kaydeder. Çıktı gelince "Doğrulanması gerekenler" listesini elle
kontrol et ve `docs/03-kaynak-dogrulama-kaydi.md` dosyasına işle.

---

## Görev 1 — 300M–700M arası Türkçe destekli modeller

```
AGENTS.md ve docs/02-model-secim-kriterleri.md dosyalarını oku.
Danışmanım 300M–700M parametre aralığındaki modellerin özellikle araştırılmasını istedi.
Bu aralıkta, K1–K5 zorunlu kriterlerini sağlayan açık ağırlıklı modelleri web'de ara.
Her model için: Hugging Face bağlantısı, parametre sayısı, Türkçe desteği (model kartında
geçiyor mu, geçen cümleyi aktar), lisans, Unsloth desteği (bağlantıyla), GGUF / Ollama durumu.
Mevcut aday listesinde olmayanları ayrıca belirt.
Sonucu arastirma/<bugünün tarihi>-kucuk-model-taramasi.md dosyasına tablo olarak yaz.
Model kartında göremediğin her bilgiyi DOĞRULANMADI diye işaretle.
```

## Görev 2 — Türkçe tıp alanında küçük model çalışmaları (literatür)

```
AGENTS.md dosyasını oku.
Türkçe tıbbi soru-cevap ya da Türkçe TUS soruları üzerinde küçük dil modelleri (≤4B) ile yapılmış
akademik çalışmaları ve Hugging Face modellerini ara. Her biri için: başlık, yazarlar, yıl,
DOI veya arXiv bağlantısı, kullanılan model ve veri seti, raporlanan sonuç.
DOI veya bağlantısını bulamadığın hiçbir çalışmayı listeye koyma.
Sonucu arastirma/<bugünün tarihi>-literatur-turkce-tip-slm.md dosyasına yaz.
```

## Görev 3 — Eksik dahiliye kılavuzları

```
AGENTS.md dosyasını oku.
Şu yan dallar için Türk uzmanlık derneklerinin güncel Türkçe klinik kılavuzlarını ara:
nefroloji, gastroenteroloji, romatoloji, enfeksiyon hastalıkları (KLİMİK).
Her biri için: dernek, kılavuz adı, yıl, doğrudan PDF bağlantısı (varsa), kullanım/telif koşulu
(sayfada yazan cümleyi aktar). Bağlantıyı açıp doğrulayamadığın hiçbir şeyi ekleme.
Sonucu arastirma/<bugünün tarihi>-eksik-kilavuzlar.md dosyasına yaz.
```

## Görev 4 — Türkçe için embedding modeli seçimi

```
AGENTS.md dosyasını oku.
BGE-M3, Qwen3-Embedding-0.6B ve EmbeddingGemma-300M modellerini karşılaştır:
parametre, vektör boyutu, maksimum girdi uzunluğu, Türkçe desteği, lisans, Ollama'da
bulunup bulunmadığı (ollama.com bağlantısıyla). Varsa Türkçe retrieval benchmark sonuçlarını
kaynağıyla ver. Sonucu arastirma/<bugünün tarihi>-embedding-karsilastirma.md dosyasına yaz.
```
