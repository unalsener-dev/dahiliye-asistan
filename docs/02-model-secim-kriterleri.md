# Model Seçim Kriterleri

Temel ilke: **istenen başarımı sağlayan en küçük model seçilir.** Küçük model hem çalıştırma
maliyetini düşürür hem de ileride mobil cihazda (edge) çalıştırmaya olanak tanır.

## Zorunlu kriterler (sağlamayan aday elenir)

| # | Kriter | Neden |
|---|---|---|
| K1 | Açık ağırlık (indirilebilir model dosyası) | Fine-tune ve yerel çalıştırma için |
| K2 | Türkçe desteği (çok dilli ön eğitim) | Kullanıcı dili Türkçe |
| K3 | Unsloth ile ücretsiz Colab'da (T4, ~15 GB) eğitilebilme | Donanım bütçesi |
| K4 | GGUF'a dönüştürülüp Ollama'da çalışabilme | Model servisi Ollama |
| K5 | Akademik kullanıma uygun lisans | Bitirme projesi |

## Değerlendirme kriterleri (adaylar arasında karşılaştırma)

| Kriter | Nasıl ölçülür |
|---|---|
| Doğruluk | turkish_mmlu TUS/dahiliye geliştirme seti |
| Kaynağa dayalı okuma | MedTurkQuAD doğrulama bölümü (EM/F1) |
| Türkçe cevap kalitesi | Elle örnek inceleme |
| Hız | Soru başına cevap süresi |
| Bellek | Çalışırken kullanılan RAM/VRAM |
| Parametre sayısı | Model kartından (Gemma 4 için efektif ve toplam ikisi birden) |

## Aday merdiveni

Her satırdaki bilgiyi model kartından kontrol et ve son iki sütunu doldur.

| Ölçek | Model | Parametre | Bağlam | Colab eğitim yöntemi | Model kartı kontrol edildi mi? | Lisans |
|---|---|---|---|---|---|---|
| ~0,3B | Gemma 3 270M | 0,27B | 32K | LoRA / QLoRA | ☐ | |
| ~0,6B | Qwen3-0.6B | 0,6B | 32K | QLoRA | ☐ | |
| ~0,8B | Qwen3.5-0.8B | 0,8B | 256K | 16-bit LoRA | ☐ | |
| ~1B | Gemma 3 1B | 1B | 32K | QLoRA | ☐ | |
| ~2B | Qwen3.5-2B | 2B | 256K | 16-bit LoRA | ☐ | |
| ~2B | Gemma 4 E2B | 2,3B efektif (5,1B toplam) | 128K | LoRA | ☐ | |
| ~4B | Qwen3.5-4B | 4B | 256K | 16-bit LoRA | ☐ | |
| ~4B | Gemma 4 E4B | 4,5B efektif (8B toplam) | 128K | QLoRA | ☐ | |

Danışman 300M–700M aralığının özellikle araştırılmasını istedi. Bu aralıkta Türkçe destekli başka
aday varsa listeye eklenir (bkz. `arastirma/` klasöründeki tarama çıktısı).

## Seçim süreci

1. **Tarama:** Tüm adaylar fine-tune edilmeden, aynı istem şablonu ve kapalı "düşünme" moduyla
   çalıştırılır. Parametre sayısına karşı doğruluk eğrisi çizilir.
2. **Doğrulama:** Taramada öne çıkan en fazla üç model aynı veri ve ayarlarla fine-tune edilir.
3. **Karar kuralı:** Fine-tuning sonrasında en başarılı adaya göre doğruluk farkı **en fazla 3 puan**
   olan **en küçük** model seçilir. (Eşik danışmanla kesinleşecek.)
