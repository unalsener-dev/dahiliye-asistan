# Embedding Modeli Karşılaştırması: BGE-M3, Qwen3-Embedding-0.6B, EmbeddingGemma-300M

- **Soru:** Üç embedding modeli parametre, vektör boyutu, maksimum girdi uzunluğu, Türkçe desteği, lisans ve
  Ollama'da bulunma açısından nasıl karşılaştırılır? Türkçe retrieval benchmark sonuçları var mı?
- **Tarih:** 2026-09-28
- **Araç:** Claude (Claude Code; WebSearch, WebFetch, makale PDF'leri `curl` + `pdftotext` ile okundu)
- **İşaretler:** Kaynak sayfasında görülemeyen bilgi **DOĞRULANMADI**, benim çıkarımım **tahmin** diye işaretlendi.

## Tablo 1 — Model özellikleri

| Özellik | BGE-M3 | Qwen3-Embedding-0.6B | EmbeddingGemma-300M |
|---|---|---|---|
| Hugging Face | [BAAI/bge-m3](https://huggingface.co/BAAI/bge-m3) | [Qwen/Qwen3-Embedding-0.6B](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B) | [google/embeddinggemma-300m](https://huggingface.co/google/embeddinggemma-300m) |
| Parametre | Kartta **yazmıyor**. Ollama etiketi `567m`; TR-TEB tablosunda "568M"; Mecellem'de "567M" | Kart: "Number of Parameters: 0.6B"; TR-TEB tablosunda "596M" | Kart: "300M parameter"; Mecellem'de "307M"; Bayram vd.'de "300.6M" |
| Vektör boyutu | Kart: "Dimension: 1024" | Kart: "Up to 1024, supports user-defined output dimensions ranging from 32 to 1024" | Kart: "768, with smaller options available (512, 256, or 128) via Matryoshka Representation Learning (MRL)" |
| Maks. girdi (token) | Kart: "Sequence Length: 8192" | Kart: 32k (Ollama sayfası da "32K") | Kart: "Maximum input context length of 2048 tokens" |
| Türkçe desteği | Kart: "more than 100 working languages"; **Türkçe adıyla geçmiyor.** Makalesinde MKQA Türkçe ("tr") üzerinde değerlendirilmiş (aşağıda) | Kart: "100+ Languages"; **Türkçe adıyla geçmiyor** | Kart: "trained with data in 100+ spoken languages"; **Türkçe adıyla geçmiyor** |
| Lisans | MIT | Apache-2.0 | Gemma lisansı ("License: gemma"). **Erişim kapılı:** "you're required to review and agree to Google's usage license" |
| Ollama | ✅ [ollama.com/library/bge-m3](https://ollama.com/library/bge-m3): `bge-m3:567m` = `latest`, 1.2GB, "8K context window" | ✅ [ollama.com/library/qwen3-embedding](https://ollama.com/library/qwen3-embedding): `qwen3-embedding:0.6b`, 639MB, "32K context window" (**`latest` 8B modeli gösteriyor, etiket açıkça yazılmalı**) | ✅ [ollama.com/library/embeddinggemma](https://ollama.com/library/embeddinggemma): `embeddinggemma:300m` = `latest`, 622MB, "2K context window"; "This model requires Ollama v0.11.10 or later" |
| Önemli kullanım notu | Model dense, sparse ve multi-vector üretebiliyor. Ollama'nın bunlardan yalnızca dense vektörü verdiği **tahmin** (sayfada yazmıyor) | Kart: "not using an `instruct` on the query side can lead to a drop in retrieval performance by approximately 1% to 5%". Ollama'da talimatın sorgu metnine elle eklenmesi gerektiği **tahmin** | Kart: "EmbeddingGemma activations do not support `float16`. Please use `float32` or `bfloat16`". Sorgu ve belge için ayrı istem şablonu var (kartta) |

## Tablo 2 — Türkçe retrieval benchmark sonuçları

**Uyarı:** Üç modeli aynı Türkçe benchmark'ta birlikte değerlendiren bir kaynak **bulunamadı**. Farklı
benchmark'ların sayıları birbirleriyle **karşılaştırılamaz** (farklı veri setleri, görevler ve ayarlar).
Aşağıdaki sayıların hepsi makale PDF'lerinin tablolarından okundu.

| Kaynak | Benchmark / metrik | BGE-M3 | Qwen3-Embedding-0.6B | EmbeddingGemma-300M | Not |
|---|---|---|---|---|---|
| Arslan vd., **TR-TEB: Turkish Text Embedding Benchmark**, LREC 2026. DOI [10.63317/3qway8hn6y53](https://doi.org/10.63317/3qway8hn6y53) · [PDF](https://aclanthology.org/2026.lrec-1.862.pdf) | TR-TEB Retrieval (nDCG@10) | **59.30** (ortalama 63.76) | **50.81** (ortalama 59.13) | Tabloda yok | Qwen3-0.6B satırında "Max Seq" **512** yazıyor, oysa model 32K destekliyor. Bu kısıtın sonucu düşürüp düşürmediği **bilinmiyor**. (Arama motoru özeti 0.6B için "retrieval 70.21" diyordu; PDF'e göre bu değer STS sütununa ait, yanlış.) |
| Uğur vd., **Mecellem Models**, arXiv:[2601.16018](https://arxiv.org/abs/2601.16018), 2026. Table 22 "Evaluation Results on MTEB-Turkish Benchmark" | MTEB-Turkish Ret. (makalede birincil metrik nDCG@10) | **54.42** (MTEB 62.87; Legal 51.16) | Tabloda yok | **55.06** (MTEB 65.42; Legal 50.63) | Hukuk alanı ağırlıklı bir değerlendirme. PDF'ten çıkarılan tabloda sütun hizası kısmen kaydı; bu iki satır tutarlı görünüyor ama elle kontrol edilmeli |
| Bayram, Diri, Yıldırım, **Adapting Multilingual Embedding Models to Turkish via Cross-Lingual Tokenizer Surgery and Offline Distillation**, arXiv:[2605.29992](https://arxiv.org/abs/2605.29992), 2026. Table 2 | TR-MTEB Retrieval (6 görev ortalaması; metrik tabloda belirtilmemiş → **DOĞRULANMADI**) | Tabloda yok | Tabloda yok | **75.9** (ortalama 65.2; 26 model içinde 4.) | Yazarların kendi TR-MTEB koşusu. Sayılar özgün TR-MTEB makalesindeki tablolarla aynı ölçekte değil |
| Chen vd., **M3-Embedding** (BGE-M3 makalesi), arXiv:[2402.03216](https://arxiv.org/abs/2402.03216), 2024. Table 2 | MKQA "tr", Recall@100 (**diller arası**: Türkçe sorgu → İngilizce Vikipedi pasajı) | Dense **75.6**; Dense+Sparse+Multi-vec **76.0** (BM25 45.8; mE5-large 74.3; OpenAI-3 71.8) | — | — | Türkçe-Türkçe arama değil. Türkçe kılavuz aramasına doğrudan yansımaz |

**Kontrol edilip bu üç modeli içermeyen kaynaklar:**
- TR-MTEB (Baysan ve Güngör, EMNLP Findings 2025, DOI [10.18653/v1/2025.findings-emnlp.471](https://doi.org/10.18653/v1/2025.findings-emnlp.471)): Tablo 2'de üç model de yok. Ancak retrieval görevleri arasında Türkçeye çevrilmiş tıbbi bir derlem olan **NFCorpus TR** var ("A medical information retrieval corpus translated into Turkish as part of this study"). Bu derlem kendi değerlendirmemiz için kullanılabilir.
- TurkEmbed (arXiv:2511.08376): özet sayfasında bu modellere ait sonuç görülmedi.

## Yorum (tahmin; ölçümle doğrulanmalı)

- **Kanıtın durumu:** BGE-M3, iki bağımsız Türkçe benchmark'ta (TR-TEB, Mecellem) retrieval'da tutarlı biçimde
  iyi. EmbeddingGemma-300M, Mecellem'de BGE-M3 ile başa baş (55.06 ve 54.42) ve yarı parametreyle çalışıyor.
  Qwen3-Embedding-0.6B'nin tek Türkçe sonucu 512 token kısıtıyla alınmış ve düşük (50.81).
- **Proje kısıtlarına göre:**
  - Lisans açısından en sorunsuz model **BGE-M3 (MIT)**.
  - **EmbeddingGemma** en küçük model (mobil/edge hedefine uygun), ancak lisansı Gemma ve erişimi kapılı.
    2K bağlam, kılavuz parçaları için büyük olasılıkla yeterli (**tahmin**; parça boyutuna bağlı).
  - **Qwen3-Embedding-0.6B** en uzun bağlamı sunuyor, ama sorgu tarafına talimat eklemek gerekiyor.
- **Öneri:** Üç modeli **kendi verimizle** ölçmek: kılavuz parçaları ile intörn tarzı sorular üzerinde
  Recall@5 ve nDCG@10. Buna ek olarak TR-MTEB içindeki NFCorpus TR. AGENTS.md gereği, dizin oluşturma ve
  sorgu aynı modelle yapılacağı için, seçim dizin kurulmadan önce kesinleşmeli.

## Doğrulanması gerekenler

- [ ] BGE-M3 parametre sayısı: HF kartında yazmıyor. 567M (Ollama) ve 568M (TR-TEB) arasındaki fark yuvarlamadan mı kaynaklanıyor?
- [ ] TR-TEB'de Qwen3-Embedding-0.6B neden 512 token ile değerlendirilmiş? Makale metninde açıklama var mı?
- [ ] Mecellem Table 22'deki BGE-M3 ve EmbeddingGemma satırlarını PDF'te gözle kontrol et (sütun hizası).
- [ ] Bayram vd. Table 2: retrieval metriği ne (nDCG@10 mu)?
- [ ] Ollama `bge-m3` sparse / multi-vector çıktılarını veriyor mu, yoksa yalnızca dense mi?
- [ ] Ollama'da `qwen3-embedding:0.6b` için sorgu talimatı nasıl verilir (metin önüne elle mi)?
- [ ] Ollama'daki vektör boyutları (sayfalarda yazmıyor): `ollama show <model>` ile `embedding_length` değerine bak.
- [ ] Gemma lisansının (EmbeddingGemma) akademik proje ve olası mobil dağıtım için koşulları.
- [ ] Üç modelin Türkçeyi adıyla listeleyen resmî bir kaynağı (teknik rapor) var mı?

## Kaynaklar

- BGE-M3 kartı: https://huggingface.co/BAAI/bge-m3 · Ollama: https://ollama.com/library/bge-m3
- Qwen3-Embedding-0.6B kartı: https://huggingface.co/Qwen/Qwen3-Embedding-0.6B · Ollama: https://ollama.com/library/qwen3-embedding
- EmbeddingGemma-300M kartı: https://huggingface.co/google/embeddinggemma-300m · Ollama: https://ollama.com/library/embeddinggemma
- TR-TEB (LREC 2026): https://aclanthology.org/2026.lrec-1.862/
- Mecellem (arXiv 2601.16018): https://arxiv.org/abs/2601.16018
- Bayram vd. (arXiv 2605.29992): https://arxiv.org/abs/2605.29992
- M3-Embedding (arXiv 2402.03216): https://arxiv.org/abs/2402.03216
- TR-MTEB (EMNLP Findings 2025): https://aclanthology.org/2025.findings-emnlp.471/
