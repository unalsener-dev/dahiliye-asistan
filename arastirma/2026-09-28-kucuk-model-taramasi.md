# Küçük Model Taraması (300M–700M parametre)

- **Soru:** 300M–700M parametre aralığında, `docs/02-model-secim-kriterleri.md` içindeki K1–K5 zorunlu
  kriterlerini sağlayan açık ağırlıklı modeller hangileri? Mevcut aday listesinde olmayan var mı?
- **Tarih:** 2026-09-28
- **Araç:** Claude (Claude Code; WebSearch + WebFetch ile model kartları okundu)
- **İstek sahibi:** Danışman, 300M–700M aralığının özellikle araştırılmasını istedi.

## Yöntem ve işaretler

- Her model için Hugging Face model kartı, gerektiğinde üreticinin blog sayfası, Unsloth belgeleri ve
  Ollama kütüphane sayfası açıldı. Aktarılan cümleler sayfadan alıntıdır (İngilizce kaldı).
- **DOĞRULANMADI** = bilgi kaynak sayfasında görülemedi. **Tahmin** = benim çıkarımım, sayfada yazmıyor.
- Sınır adaylar da tabloya alındı: Gemma 3 270M (aralığın hemen altında, zaten aday listesinde) ve
  Qwen3.5-0.8B (aralığın hemen üstünde, bkz. "Aralık dışı" bölümü).
- K3 (T4'te eğitilebilme): 1B altındaki tüm modellerin 15 GB T4'e sığacağı **tahmindir**; ölçülmedi.
  Ölçüm önerisi: her model için Unsloth ile 50 adımlık deneme eğitimi ve `torch.cuda.max_memory_allocated()`.

## Tablo 1 — Kriterleri sağlayan / sağlama olasılığı olan adaylar

| Model | Hugging Face | Parametre (karttan) | Türkçe desteği (kartta geçen cümle) | Lisans | Unsloth desteği | GGUF / Ollama | Aday listesinde mi? |
|---|---|---|---|---|---|---|---|
| Qwen3-0.6B | [Qwen/Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) | "Number of Parameters: 0.6B", "Non-Embedding: 0.44B" | Kartta: "Support of 100+ languages and dialects" — **Türkçe adıyla kartta geçmiyor.** Üreticinin [Qwen3 blogunda](https://qwenlm.github.io/blog/qwen3/) "119 languages and dialects" tablosunda Türk dilleri satırı: "Turkish, North Azerbaijani, Northern Uzbek, Kazakh, Bashkir, Tatar" | Apache-2.0 | Var: [Unsloth Qwen3 rehberi](https://unsloth.ai/docs/models/tutorials/qwen3-how-to-run-and-fine-tune), [unsloth/Qwen3-0.6B-unsloth-bnb-4bit](https://huggingface.co/unsloth/Qwen3-0.6B-unsloth-bnb-4bit) | GGUF: [unsloth/Qwen3-0.6B-GGUF](https://huggingface.co/unsloth/Qwen3-0.6B-GGUF). Ollama: [`qwen3:0.6b`](https://ollama.com/library/qwen3) (523 MB) | ✅ Evet |
| Qwen2.5-0.5B-Instruct | [Qwen/Qwen2.5-0.5B-Instruct](https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct) | "Number of Parameters: 0.49B", "Non-Embedding: 0.36B" | Kartta: "Multilingual support for over 29 languages, including Chinese, English, French, Spanish, Portuguese, German, Italian, Russian, Japanese, Korean, Vietnamese, Thai, Arabic, and more." — **Türkçe adıyla geçmiyor → DOĞRULANMADI.** [Qwen2.5 blogunda](https://qwenlm.github.io/blog/qwen2.5-llm/) Türkçe yalnızca değerlendirme tablosunda (TurkishMMLU) geçiyor, destek beyanı olarak değil. | Apache-2.0 | Var (katalogda): [unsloth/Qwen2.5-0.5B-Instruct-bnb-4bit](https://huggingface.co/unsloth/Qwen2.5-0.5B-Instruct-bnb-4bit), [Unsloth model kataloğu](https://unsloth.ai/docs/get-started/unsloth-model-catalog) | Ollama: [`qwen2.5:0.5b`](https://ollama.com/library/qwen2.5) (398 MB). Resmî GGUF deposu: DOĞRULANMADI | ❌ Hayır (yeni) |
| Gemma 3 270M (sınır, <300M) | [google/gemma-3-270m-it](https://huggingface.co/google/gemma-3-270m-it) | "270M" (kartta "the 270M with 6 trillion tokens") | Kartta: "multilingual support in over 140 languages", "The training dataset includes content in over 140 languages." — **Türkçe adıyla geçmiyor → DOĞRULANMADI** | Gemma lisansı ("License: gemma"). Erişim kapılı: "you have to accept the conditions to access its files and content". Akademik kullanıma uygunluğu: DOĞRULANMADI (lisans metni okunmalı) | Var: [Unsloth Gemma 3 rehberi](https://unsloth.ai/docs/models/tutorials/gemma-3-how-to-run-and-fine-tune), [unsloth/gemma-3-270m-it](https://huggingface.co/unsloth/gemma-3-270m-it). Colab defteri bağlantısı arama sonucunda görüldü, sayfa açılmadı: [Gemma3_(270M).ipynb](https://colab.research.google.com/github/unslothai/notebooks/blob/main/nb/Gemma3_(270M).ipynb) | GGUF: [unsloth/gemma-3-270m-it-GGUF](https://huggingface.co/unsloth/gemma-3-270m-it-GGUF). Ollama: [`gemma3:270m`](https://ollama.com/library/gemma3) (292 MB, 32K bağlam) | ✅ Evet |
| turkish-gpt2-medium-350m-instruct-v0.1 (YTÜ COSMOS) | [ytu-ce-cosmos/turkish-gpt2-medium-350m-instruct-v0.1](https://huggingface.co/ytu-ce-cosmos/turkish-gpt2-medium-350m-instruct-v0.1) | Hugging Face rozeti: "0.4B params" (model adı 350M diyor) | Türkçe'ye özel model; kart: "Turkish Language Model finetuned with a dataset consisting of 35K instructions" | MIT | **DOĞRULANMADI** — Unsloth belgelerinde GPT-2 mimarisi adıyla geçmiyor, bu model için Unsloth defteri/yüklemesi bulunamadı | GGUF: kartta "quantized versions" bağlantısı var, ayrıntı **DOĞRULANMADI**. Ollama: **DOĞRULANMADI** | ❌ Hayır (yeni) |
| TURKLM 443M-SFT | [ArdaAydogdu/turklm-443m-sft](https://huggingface.co/ArdaAydogdu/turklm-443m-sft) | "443.07 Milyon" | Türkçe'ye özel, sıfırdan eğitilmiş; kart: "64.000 kelime dağarcığına sahip, Türkçe heceleme ve ek yapısına uygun BPE tokenizer" | Apache-2.0. **Dikkat:** kartta tıbbi, finansal ve hukuki tavsiye için kullanılamayacağı belirtiliyor | **DOĞRULANMADI.** Kartta yalnızca Hugging Face'in otomatik "Unsloth Desktop" düğmesi var (bu bir eğitim desteği kanıtı değil). LLaMA mimarisinde olduğu için Unsloth'la çalışabileceği **tahmin** | GGUF: kartta "turklm-443m-sft-Q4_K_M.gguf" (283 MB). Ollama: kartta "Ollama & LM Studio Entegrasyonu" başlığında talimat var | ❌ Hayır (yeni) |

### Tablo 1'in K1–K5 özeti

✅ = kaynakta görüldü · ❓ = DOĞRULANMADI / tahmin · ⚠️ = koşullu

| Model | K1 Açık ağırlık | K2 Türkçe | K3 Unsloth + T4 | K4 GGUF + Ollama | K5 Lisans | Not |
|---|---|---|---|---|---|---|
| Qwen3-0.6B | ✅ | ✅ (blogda adıyla, kartta değil) | ✅ Unsloth / ❓ T4 bellek | ✅ | ✅ Apache-2.0 | Aralıktaki en güçlü aday |
| Qwen2.5-0.5B-Instruct | ✅ | ❓ | ✅ Unsloth / ❓ T4 bellek | ✅ Ollama | ✅ Apache-2.0 | Qwen3-0.6B'nin eski kuşağı; karşılaştırma tabanı olarak işe yarar |
| Gemma 3 270M | ✅ (kapılı erişim) | ❓ ("140+ dil" diyor, Türkçe adı yok) | ✅ Unsloth / ❓ T4 bellek | ✅ | ⚠️ Gemma lisansı okunmalı | 300M'nin altında |
| turkish-gpt2-medium-350m-instruct | ✅ | ✅ | ❓ | ❓ | ✅ MIT | Bağlam uzunluğu kartta yok. GPT-2 medium'un özgün bağlamı 1024 token (hatırladığım bilgi, **tahmin**); RAG için dar olabilir |
| TURKLM 443M-SFT | ✅ | ✅ | ❓ | ✅ | ⚠️ Apache-2.0, ancak kartta tıbbi kullanım dışlanıyor | Bağlam "2048 token"; eğitim verisi "yaklaşık 1,3 milyar token"; kişisel proje (kurum değil) |

## Tablo 2 — Aralıkta olup K2 (Türkçe) nedeniyle elenen modeller

| Model | Hugging Face | Parametre | Kartta geçen dil cümlesi | Lisans | Unsloth / GGUF / Ollama (bilgi amaçlı) | Aday listesinde mi? |
|---|---|---|---|---|---|---|
| LFM2.5-350M (Liquid AI) | [LiquidAI/LFM2.5-350M](https://huggingface.co/LiquidAI/LFM2.5-350M) | "350M" | "English, Arabic, Chinese, French, German, Japanese, Korean, Portuguese, Spanish" — Türkçe yok | lfm1.0 (LFM Open License) | Kartta Unsloth SFT/CPT/GRPO defterleri ve GGUF var. Ollama: [LiquidAI/lfm2.5-350m](https://ollama.com/LiquidAI/lfm2.5-350m) | ❌ Hayır |
| LFM2-700M (Liquid AI) | [LiquidAI/LFM2-700M](https://huggingface.co/LiquidAI/LFM2-700M) | "742,489,344" (aralığın biraz üstünde) | "English, Arabic, Chinese, French, German, Japanese, Korean, and Spanish." — Türkçe yok | LFM Open License v1.0 | Kartta [Unsloth SFT defteri](https://colab.research.google.com/drive/1HROdGaPFt1tATniBcos11-doVaH7kOI3?usp=sharing) ve [GGUF](https://huggingface.co/LiquidAI/LFM2-700M-GGUF) var | ❌ Hayır |
| Granite 4.0 350M (IBM) | [ibm-granite/granite-4.0-350m](https://huggingface.co/ibm-granite/granite-4.0-350m) | "350M" | "English, German, Spanish, French, Japanese, Portuguese, Arabic, Czech, Italian, Korean, Dutch, and Chinese." — Türkçe yok | Apache-2.0 | GGUF: [unsloth/granite-4.0-350m-GGUF](https://huggingface.co/unsloth/granite-4.0-350m-GGUF) | ❌ Hayır |
| SmolLM2-360M-Instruct | [HuggingFaceTB/SmolLM2-360M-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-360M-Instruct) | "360M parameters" | "primarily understand and generate content in English" | Apache-2.0 | Unsloth kataloğunda var: [GGUF](https://huggingface.co/unsloth/SmolLM2-360M-Instruct-GGUF), [4-bit](https://huggingface.co/unsloth/SmolLM2-360M-Instruct-bnb-4bit) | ❌ Hayır |
| ERNIE-4.5-0.3B (Baidu) | [baidu/ERNIE-4.5-0.3B-PT](https://huggingface.co/baidu/ERNIE-4.5-0.3B-PT) | "0.36B" | Kartta yalnızca İngilizce ve Çince listeleniyor | Apache-2.0 | DOĞRULANMADI | ❌ Hayır |
| Falcon-H1-0.5B-Instruct (TII) | [tiiuae/Falcon-H1-0.5B-Instruct](https://huggingface.co/tiiuae/Falcon-H1-0.5B-Instruct) | "0.5B params" | Kartta yalnızca İngilizce görüldü, Türkçe yok | Falcon-LLM License | Kartta llama.cpp uyumlu GGUF koleksiyonu belirtiliyor | ❌ Hayır |
| BLOOMZ-560M | [bigscience/bloomz-560m](https://huggingface.co/bigscience/bloomz-560m) | "560M" | "46 languages"; Türkçe listede yok | bigscience-bloom-rail-1.0 | DOĞRULANMADI | ❌ Hayır |

## Aralık dışı ama ilgili notlar

- **Qwen3.5-0.8B** ([kart](https://huggingface.co/Qwen/Qwen3.5-0.8B)): "Number of Parameters: 0.8B", Apache-2.0,
  "Expanded support to 201 languages and dialects". Türkçe kartta adıyla geçmiyor. Aday listesinde zaten var.
- **Daha yeni Qwen kuşakları:** [Qwen3.8 GitHub](https://github.com/QwenLM/Qwen3.8) sayfasında yalnızca 27B ve
  2.4T-A95B duyurulmuş; 1B altında Qwen3.8 modeli yok (2026-09-28 itibarıyla). Qwen3.6 küçük boyutları bu
  taramada kontrol edilmedi → DOĞRULANMADI.
- **Gemma 4:** En küçük sürüm E2B, yani aralığın çok üstünde (aday listesinde zaten var).
- **turkish-gpt2-large-750m-instruct-v0.1** ([kart](https://huggingface.co/ytu-ce-cosmos/turkish-gpt2-large-750m-instruct-v0.1)):
  adı 750M olduğu için aralığın hemen üstünde; kartı ayrıntılı açılmadı → DOĞRULANMADI.
- **TurkishLLM-Generative-V1** ([kart](https://huggingface.co/Haxxord/TurkishLLM-Generative-V1)): "~52.5M" parametre, yani
  aralığın çok altında. Kartta Türkiye'nin başkentini "Beyrut" diye cevapladığı bir hata örneği var ve
  "parametrik hafızası bağımsız olgusal soru-cevap için yetersiz" deniyor. Bu yüzden elendi.

## Mevcut aday listesinde olmayan modeller (özet)

`docs/02-model-secim-kriterleri.md` aday merdivenine eklenmesi **önerilebilecek** modeller, doğrulandıktan sonra:

1. **Qwen2.5-0.5B-Instruct:** Kriterlerin çoğunu sağlıyor ama Türkçe desteği kartta adıyla geçmiyor. Qwen3-0.6B ile
   aynı aileden olduğu için "önceki kuşak" karşılaştırması sağlar.
2. **turkish-gpt2-medium-350m-instruct-v0.1:** Türkçe'ye özel ve MIT lisanslı. Unsloth ve Ollama desteği doğrulanmadı.
3. **TURKLM 443M-SFT:** Türkçe'ye özel, GGUF'u ve Ollama talimatı var. Ancak tıbbi kullanım kartta dışlanıyor ve
   bağlam 2048 token. Kişisel bir proje olduğu için güvenilirliği ayrıca değerlendirilmeli.

Türkçe'ye özel iki model, "çok dilli genel model mi, küçük Türkçe'ye özel model mi?" karşılaştırması için
ilginç. Yine de eğitim verileri çok küçük (35K talimat, ~1,3 milyar token). Bu nedenle genel çok dilli modellerden
geride kalmaları **tahmin** edilir; ölçmek için turkish_mmlu TUS alt kümesinde tarama yapılmalı.

## Doğrulanması gerekenler

- [ ] Qwen3-0.6B: Türkçe desteği kartta değil, [Qwen3 blogunda](https://qwenlm.github.io/blog/qwen3/) geçiyor. Blog tablosundaki satırı elle kontrol et.
- [ ] Qwen2.5-0.5B-Instruct: "29 languages" listesinde Türkçe var mı? Resmî kaynakta (kart / blog / teknik rapor) ara.
- [ ] Gemma 3 270M: "140+ languages" içinde Türkçe'nin adıyla geçtiği bir kaynak (Gemma 3 teknik raporu) var mı?
- [ ] Gemma lisansının (Gemma Terms of Use) akademik bitirme projesine uygunluğunu lisans metninden oku.
- [ ] Gemma 3 270M Unsloth Colab defteri bağlantısının açıldığını ve T4'te çalıştığını kontrol et.
- [ ] Qwen2.5-0.5B-Instruct için resmî GGUF deposu var mı? (`Qwen/Qwen2.5-0.5B-Instruct-GGUF`, hatırladığım bilgi, sayfa açılmadı)
- [ ] turkish-gpt2-medium-350m-instruct: bağlam uzunluğu, GGUF dosyası, Unsloth ile GPT-2 eğitimi ve Ollama'da çalışma.
- [ ] TURKLM 443M-SFT: Unsloth ile LoRA eğitimi gerçekten çalışıyor mu? Karttaki tıbbi kullanım sınırı, bitirme projesinde (araştırma amaçlı) kullanmaya engel mi? Danışmana sor.
- [ ] Falcon-H1-0.5B-Instruct: dil listesi kartta yalnızca İngilizce mi? (Falcon-H1 ailesinin büyük modelleri daha çok dil destekliyor olabilir; **tahmin**)
- [ ] Qwen3.6 serisinde 1B altı model var mı?
- [ ] Tüm adaylar için T4'te (15 GB) gerçek bellek kullanımı: ölçülmedi (K3).
- [ ] Hugging Face'te `language:tr` + parametre filtresiyle ek tarama yap; bu tarama arama motoru sonuçlarıyla sınırlıydı ve eksik olabilir.

## Kaynaklar

- Qwen3-0.6B kartı: https://huggingface.co/Qwen/Qwen3-0.6B
- Qwen3 blogu (119 dil tablosu): https://qwenlm.github.io/blog/qwen3/
- Qwen2.5-0.5B-Instruct kartı: https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct
- Qwen2.5 blogu: https://qwenlm.github.io/blog/qwen2.5-llm/
- Qwen3.5-0.8B kartı: https://huggingface.co/Qwen/Qwen3.5-0.8B
- Qwen3.8 GitHub: https://github.com/QwenLM/Qwen3.8
- Gemma 3 270M kartı: https://huggingface.co/google/gemma-3-270m-it
- YTÜ COSMOS GPT-2 350M instruct: https://huggingface.co/ytu-ce-cosmos/turkish-gpt2-medium-350m-instruct-v0.1
- TURKLM 443M-SFT: https://huggingface.co/ArdaAydogdu/turklm-443m-sft
- LFM2.5-350M: https://huggingface.co/LiquidAI/LFM2.5-350M
- LFM2-700M: https://huggingface.co/LiquidAI/LFM2-700M
- Granite 4.0 350M: https://huggingface.co/ibm-granite/granite-4.0-350m
- SmolLM2-360M-Instruct: https://huggingface.co/HuggingFaceTB/SmolLM2-360M-Instruct
- ERNIE-4.5-0.3B: https://huggingface.co/baidu/ERNIE-4.5-0.3B-PT
- Falcon-H1-0.5B-Instruct: https://huggingface.co/tiiuae/Falcon-H1-0.5B-Instruct
- BLOOMZ-560M: https://huggingface.co/bigscience/bloomz-560m
- TurkishLLM-Generative-V1: https://huggingface.co/Haxxord/TurkishLLM-Generative-V1
- Unsloth model kataloğu: https://unsloth.ai/docs/get-started/unsloth-model-catalog
- Unsloth Qwen3 rehberi: https://unsloth.ai/docs/models/tutorials/qwen3-how-to-run-and-fine-tune
- Unsloth Gemma 3 rehberi: https://unsloth.ai/docs/models/tutorials/gemma-3-how-to-run-and-fine-tune
- Ollama qwen3: https://ollama.com/library/qwen3
- Ollama qwen2.5: https://ollama.com/library/qwen2.5
- Ollama gemma3: https://ollama.com/library/gemma3
