# 300M–700M Açık Ağırlıklı Model Taraması

- **Soru:** Danışmanın isteğiyle 300M–700M parametre aralığında, `docs/02-model-secim-kriterleri.md` içindeki K1–K5 zorunlu kriterlerine uyan modeller hangileri? Mevcut aday listesinde olmayanlar hangileri?
- **Tarih:** 2026-09-28
- **Araç:** Codex (web araması ve kaynak sayfalarının incelenmesi)

## Kriterler ve yorum

K1 indirilebilir açık ağırlık, K2 çok dilli ön eğitim/Türkçe desteği, K3 Unsloth ile ücretsiz Colab T4 (~15 GB) üzerinde eğitim, K4 GGUF'a dönüştürme ve Ollama'da çalıştırma, K5 akademik kullanıma uygun lisanstır. Aşağıdaki iki Qwen modelinde ağırlık dosyaları, Apache-2.0 lisansı ve Unsloth desteği doğrulanıyor. Model kartları Türkçeyi adıyla belirtmiyor; kartlardaki çok dillilik beyanı K2'nin çok dilli ön eğitim kısmı için kanıt, Türkçe özelindeki yetkinlik için tek başına kanıt değildir. T4 üzerinde gerçek eğitim denemesi yapılmadı; bu nedenle K3 donanım koşulu **DOĞRULANMADI**.

## Kriterlere uyan adaylar

| Model | Hugging Face / parametre | Türkçe desteği: kartta geçen cümle | Lisans | Unsloth / K3 | GGUF / Ollama | Mevcut aday listesi |
|---|---|---|---|---|---|---|
| Qwen3-0.6B | [Qwen/Qwen3-0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) — kart: “Number of Parameters: 0.6B”; `safetensors` dosyaları mevcut (K1). | Kartta: “Support of 100+ languages and dialects with strong capabilities for multilingual instruction following and translation.” Türkçe adı bu cümlede veya kart metninde geçmiyor: **DOĞRULANMADI**. | Apache-2.0 ([kart](https://huggingface.co/Qwen/Qwen3-0.6B), lisans etiketi). | [Unsloth Qwen3 eğitim rehberi](https://unsloth.ai/docs/models/tutorials/qwen3-how-to-run-and-fine-tune) ve [Unsloth Qwen3-0.6B 4-bit ağırlıkları](https://huggingface.co/unsloth/Qwen3-0.6B-unsloth-bnb-4bit) mevcut. Unsloth ile eğitim desteği doğrulandı; ücretsiz Colab T4'te bellek yeterliliği ve başarılı eğitim: **DOĞRULANMADI**. | Kart yerel kullanım için Ollama/llama.cpp desteğini belirtiyor; [Ollama Qwen3 kütüphanesinde](https://ollama.com/library/qwen3) `0.6b` etiketi var. GGUF kuantizasyonları HF model sayfasındaki quantization bağlantısından bulunabiliyor. | **Evet** — `docs/02-model-secim-kriterleri.md` merdiveninde var. |
| Qwen2.5-0.5B-Instruct | [Qwen/Qwen2.5-0.5B-Instruct](https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct) — kart: “Number of Parameters: 0.49B”; “Non-Embedding: 0.36B”; `safetensors` dosyaları mevcut (K1). | Kartta: “Multilingual support for over 29 languages, including Chinese, English, French, Spanish, Portuguese, German, Italian, Russian, Japanese, Korean, Vietnamese, Thai, Arabic, and more.” Türkçe adı listelenmiyor: **DOĞRULANMADI**. | Apache-2.0 ([kart](https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct), lisans etiketi). | [Unsloth model kataloğunda](https://unsloth.ai/docs/get-started/unsloth-model-catalog) Qwen2.5 0.5B eğitim/4-bit seçeneği listeleniyor. Unsloth ile eğitim desteği doğrulandı; ücretsiz Colab T4'te bellek yeterliliği ve başarılı eğitim: **DOĞRULANMADI**. | [Ollama Qwen2.5 kütüphanesinde](https://ollama.com/library/qwen2.5) `0.5b` seçeneği mevcut. GGUF dönüştürme Unsloth dokümanındaki [GGUF dışa aktarma](https://unsloth.ai/docs/basics/inference-and-deployment/gguf) akışıyla destekleniyor; model kartında üreticiye ait ayrı GGUF deposu: **DOĞRULANMADI**. | **Hayır** — aday merdiveninde yer almıyor. |

### Kriter durumunun özeti

| Model | K1 açık ağırlık | K2 çok dillilik / Türkçe | K3 Unsloth + T4 | K4 GGUF + Ollama | K5 lisans |
|---|---|---|---|---|---|
| Qwen3-0.6B | Doğrulandı | Çok dilli kart beyanı doğrulandı; Türkçe adı kartta **DOĞRULANMADI** | Unsloth doğrulandı; T4 başarımı **DOĞRULANMADI** | Doğrulandı | Apache-2.0 |
| Qwen2.5-0.5B-Instruct | Doğrulandı | Çok dilli kart beyanı doğrulandı; Türkçe adı kartta **DOĞRULANMADI** | Unsloth doğrulandı; T4 başarımı **DOĞRULANMADI** | Doğrulandı | Apache-2.0 |

Bu nedenle modeller K1, K4 ve K5'i kaynakla karşılıyor. K2 genel çok dillilik düzeyinde karşılanıyor; Türkçe özelindeki açık kart kanıtı eksik. K3'ün Unsloth kısmı karşılanıyor, ancak kriterdeki ücretsiz T4 donanım koşulu deneyle henüz doğrulanmadı. “K1–K5 kesin olarak geçti” sonucu çıkarılmamalı; T4 denemesi ve Türkçe dil kanıtı/benchmark kontrolü gereklidir.

## Aralıkta taranıp zorunlu kriteri doğrulanamayan ilgili modeller

| Model | Neden dahil edilmedi | Kaynak |
|---|---|---|
| `ytu-ce-cosmos/turkish-gpt2-medium-350m-instruct-v0.1` | Kart Türkçe model ve 35K talimatla ince ayarlandığını söylüyor. Ancak Unsloth ile bu GPT-2 modelinde eğitim ve T4 uyumu kaynakla doğrulanamadı; K3 karşılanmış sayılamaz. MIT lisansı belirtiliyor. | [Model kartı](https://huggingface.co/ytu-ce-cosmos/turkish-gpt2-medium-350m-instruct-v0.1) |
| `ArdaAydogdu/turklm-443m-sft` | Kart Türkçeye özel olduğunu ve GGUF/Ollama kullanımını anlatıyor; Unsloth eğitimi doğrulanamadı. Kartta tıbbi tavsiye amacıyla kullanımı dışlayan uyarı da bulunuyor. | [Model kartı](https://huggingface.co/ArdaAydogdu/turklm-443m-sft) |
| `HuggingFaceTB/SmolLM2-360M-Instruct` | Kart modelin öncelikle İngilizce içerik anladığını/ürettiğini belirtiyor; K2 için yeterli Türkçe kanıtı yok. | [Model kartı](https://huggingface.co/HuggingFaceTB/SmolLM2-360M-Instruct) |
| LFM2.5-350M, Granite 4.0 350M, BLOOMZ-560M ve diğer incelenen küçük modeller | Kartların listelenen dil beyanları Türkçeyi içermiyor veya K2 Türkçe desteği kartta doğrulanamadı. Kriterleri sağlıyorlar diye sunulmadı. | [LFM2.5 kartı](https://huggingface.co/LiquidAI/LFM2.5-350M), [Granite kartı](https://huggingface.co/ibm-granite/granite-4.0-350m), [BLOOMZ kartı](https://huggingface.co/bigscience/bloomz-560m) |

## Mevcut aday listesinde olmayanlar

300M–700M aralığındaki Qwen3-0.6B zaten aday merdiveninde bulunuyor. **Qwen2.5-0.5B-Instruct** merdivende yok; karşılaştırma adayı olarak eklenebilir, ancak Türkçe desteği ile T4 eğitim koşulu doğrulanmadan zorunlu kriterleri kesin karşılamış sayılmamalıdır. Türkçe GPT-2 350M ve TURKLM 443M de listede yok; fakat Unsloth/T4 koşulu doğrulanmadığı için bu taramada kriterleri geçenler arasına alınmadı.

## Doğrulanması gerekenler

- [ ] Qwen3 ve Qwen2.5 kartlarında Türkçe adı açıkça yer almıyor; Türkçe dil başarımını Türkçe değerlendirme setinde ölç.
- [ ] İki Qwen modelinde Unsloth ile ücretsiz Colab T4 üzerinde kısa eğitim denemesi yap; tepe VRAM kullanımını kaydet. Mevcut kaynaklar bu donanım koşulunu doğrulamıyor.
- [ ] Akademik kullanım/lisans kararını projedeki lisans inceleme süreciyle teyit et; raporda HF'nin Apache-2.0 lisans etiketi esas alındı.
- [ ] Qwen2.5-0.5B-Instruct için üreticinin ayrı GGUF deposu olup olmadığını kontrol et; burada doğrulanan yol Unsloth dönüştürmesi ve Ollama kütüphane kaydıdır.

## Kaynaklar

- [Model seçim ölçütleri](../docs/02-model-secim-kriterleri.md)
- [Qwen3-0.6B model kartı](https://huggingface.co/Qwen/Qwen3-0.6B)
- [Qwen2.5-0.5B-Instruct model kartı](https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct)
- [Unsloth Qwen3 rehberi](https://unsloth.ai/docs/models/tutorials/qwen3-how-to-run-and-fine-tune)
- [Unsloth model kataloğu](https://unsloth.ai/docs/get-started/unsloth-model-catalog)
- [Unsloth GGUF dışa aktarma](https://unsloth.ai/docs/basics/inference-and-deployment/gguf)
- [Ollama Qwen3](https://ollama.com/library/qwen3) · [Ollama Qwen2.5](https://ollama.com/library/qwen2.5)
