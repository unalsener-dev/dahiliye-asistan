# Literatür Taraması: Türkçe Tıbbi Soru-Cevap ve TUS Üzerinde Küçük Dil Modelleri (≤4B)

- **Soru:** Türkçe tıbbi soru-cevap ya da Türkçe TUS soruları üzerinde küçük dil modelleriyle (≤4B parametre)
  yapılmış akademik çalışmalar ve Hugging Face modelleri hangileri? Hangi model ve veri seti kullanılmış, hangi
  sonuç raporlanmış?
- **Tarih:** 2026-09-28
- **Araç:** Claude (Claude Code; WebSearch, WebFetch, arXiv API, Hugging Face API)
- **Kural:** DOI'si veya bağlantısı bulunamayan çalışma listeye alınmadı. Sayfasında görülemeyen bilgi
  **DOĞRULANMADI**, benim çıkarımım **tahmin** diye işaretlendi.

## Kısa sonuç

1. **Bu taramada, üretken (generative) ≤4B bir dil modelinin TUS veya Türkçe tıbbi soru-cevap üzerinde
   değerlendirildiği hakemli bir çalışma bulunamadı.** Bulunan TUS çalışmalarının hepsi büyük ya da kapalı
   modelleri (GPT-4/4o, Gemini, Llama 3 70B, Command R+) kullanıyor.
2. ≤4B ölçütünü sağlayan tek akademik çalışma, **BERTurk** (kodlayıcı, ~0,1–0,2B) ile **çıkarımsal**
   (extractive) soru-cevap yapan MedTurkQuAD çalışması (İncidelen ve Aydoğan, 2024).
3. Hugging Face'te ≤4B birkaç Türkçe tıbbi model var (BERTurk, Gemma 3n E2B ve Kumru-2B tabanlı). Bunların
   hiçbirinin model kartında üretken soru-cevap için değerlendirme sonucu yok.
4. Bu boşluk, projenin araştırma sorusunun (en küçük yeterli model) literatürde henüz yanıtlanmadığını
   gösteriyor. Bu bir **yorum**, yayımlanmış bir iddia değil. Tarama, arama motoru ve arXiv sonuçlarıyla
   sınırlıydı; Google Scholar ve DergiPark'ta ayrıca aranmalı.

## Tablo 1 — ≤4B modelle yapılmış akademik çalışmalar

| Başlık | Yazarlar | Yıl | DOI / bağlantı | Kullanılan model | Veri seti | Raporlanan sonuç |
|---|---|---|---|---|---|---|
| Developing Question-Answering Models in Low-Resource Languages: A Case Study on Turkish Medical Texts Using Transformer-Based Approaches | M. İncidelen, M. Aydoğan | 2024 (8th IDAP Symposium) | [10.1109/IDAP64064.2024.10711128](https://doi.org/10.1109/IDAP64064.2024.10711128) | BERTurk türevleri (kodlayıcı, çıkarımsal QA). En iyi sonuç `dbmdz/bert-base-turkish-128k-cased` tabanlı modelde (HF kartında "0.2B params") | MedTurkQuAD: 8.200 soru-cevap çifti, kaynakları Türkçe Vikipedi ve tıp tezleri | BERTurk (cased, 128k): **EM 55,121 / F1 77,187.** Kaynak: [HF model kartı](https://huggingface.co/incidelen/bert-base-turkish-128k-cased-medical-qa) ve arama sonucu özeti. IEEE sayfası içerik göstermedi → özet metni **DOĞRULANMADI** |

**Not:** Bu çalışma üretken bir dil modeli kullanmıyor; cevabı verilen metinden kesip çıkarıyor. Yine de projenin
"Kaynağa dayalı okuma" ölçütü için (MedTurkQuAD EM/F1) doğrudan **karşılaştırma tabanı** olarak kullanılabilir.

## Tablo 2 — Hugging Face modelleri (≤4B, Türkçe tıbbi QA)

| Model | Geliştirici | Bağlantı | Taban model / boyut | Veri seti | Lisans (kart) | Raporlanan sonuç |
|---|---|---|---|---|---|---|
| MedBERTurkQA 128k | incidelen | [incidelen/bert-base-turkish-128k-cased-medical-qa](https://huggingface.co/incidelen/bert-base-turkish-128k-cased-medical-qa) | `dbmdz/bert-base-turkish-128k-cased`, "0.2B" | MedTurkQuAD | CC-BY-4.0 | EM 55,121 / F1 77,187. Makale DOI'si kartta: 10.1109/IDAP64064.2024.10711128 |
| turkish-medical-question-answering | kaixkhazaki | [kaixkhazaki/turkish-medical-question-answering](https://huggingface.co/kaixkhazaki/turkish-medical-question-answering) | `dbmdz/bert-base-turkish-cased`, "0.1B" (çıkarımsal QA) | MedTurkQuAD | MIT | EM 52,79 / F1 76,14 (doğrulama F1 76,17). Kendi makalesi yok; kart İncidelen ve Aydoğan (2024) çalışmasına atıf yapıyor |
| gemma-3n-E2B-Turkish-Medical-QA | hoatac | [hoatac/gemma-3n-E2B-Turkish-Medical-QA](https://huggingface.co/hoatac/gemma-3n-E2B-Turkish-Medical-QA) | `unsloth/gemma-3n-e2b-it-unsloth-bnb-4bit` (Unsloth ile eğitilmiş). Parametre sayısı kartta yok → **DOĞRULANMADI** | Kartta yok → **DOĞRULANMADI** | Apache-2.0 (kartta; taban Gemma 3n'in kendi lisansıyla çelişiyor olabilir → **DOĞRULANMADI**) | **Yok** |
| Kumru-Turkish-Medical-2B-QA-4bit-Mutlu-5K | hoatac | [hoatac/Kumru-Turkish-Medical-2B-QA-4bit-Mutlu-5K](https://huggingface.co/hoatac/Kumru-Turkish-Medical-2B-QA-4bit-Mutlu-5K) | "2B params". Taban model kartta yazmıyor; adından Kumru-2B olduğu **tahmin** | Kartta yok ("[More Information Needed]") | Kartta yok | **Yok** |
| fine-tuned-t5-small-turkish-mmlu | cuneytkaya | [cuneytkaya/fine-tuned-t5-small-turkish-mmlu](https://huggingface.co/cuneytkaya/fine-tuned-t5-small-turkish-mmlu) | `google-t5/t5-small`, "60.5M" | Turkish MMLU (Bayram, 2024); kartta KPSS ve TUS içerdiği belirtiliyor | Apache-2.0 | Yalnızca eğitim kaybı: "0.0749". Test kümesi sonucu yok, bu yüzden başarım göstergesi sayılamaz |

**Eleme notu:** Aynı geliştiricinin `hoatac/gemma-3n-Turkish-Medical-QA-Merged` modeli Gemma 3n **E4B** tabanlı
(kartta "8B"), bu yüzden ≤4B dışında kaldı. Hugging Face'te bulunan diğer "turkish-medical" modelleri
(Llama 3 8B, Qwen2.5 7B, Phi-4, 14B türevleri) boyut nedeniyle alınmadı. `selincildam/medical-chatbot-turkish`
modelinin kartı boş olduğu için boyutu belirlenemedi.

## Tablo 3 — İlgili ama kapsam dışı çalışmalar (>4B ya da ≤4B sonucu yok)

Bağlam için listelendi; ≤4B ölçütünü **sağlamıyorlar**.

| Başlık | Yazarlar | Yıl | DOI / bağlantı | Model | Veri seti | Raporlanan sonuç |
|---|---|---|---|---|---|---|
| The role of artificial intelligence in medical education: an evaluation of LLMs on the Turkish Medical Specialty Training Entrance Exam | Murat Koçak, Ali Kemal Oğuz, Zafer Akçalı | 2025 (BMC Medical Education) | [10.1186/s12909-025-07148-0](https://doi.org/10.1186/s12909-025-07148-0) | ChatGPT-4, Gemini 1.5 Pro, Command R+, Llama 3 70B | TUS 2021/1. dönem, 240 soru (120 temel + 120 klinik) | ChatGPT-4 %88,75; Llama 3 70B %79,17; Gemini 1.5 Pro %78,13; Command R+ %50,00. Adayların ortalaması %48,16 |
| Tıpta uzmanlık sınavında (TUS) büyük dil modelleri insanlardan daha mı başarılı? | Yeşim Aygül, Müge Olucoğlu, Adil Alpkoçak | 2024 | [arXiv:2408.12305](https://arxiv.org/abs/2408.12305) | Gemini, ChatGPT-4, ChatGPT-4o | TUS 2021, 240 soru | Klinik: Gemini 82, ChatGPT-4 105, ChatGPT-4o 117 doğru. Temel: Gemini 93, ChatGPT-4 93, ChatGPT-4o 107 doğru |
| Setting Standards in Turkish NLP: TR-MMLU for Large Language Model Evaluation | M. Ali Bayram, Ali Arda Fincan, Ahmet Semih Gümüş, Banu Diri, Savaş Yıldırım, Öner Aytaş | 2025 | [arXiv:2501.00593](https://arxiv.org/abs/2501.00593) | 39 LLM değerlendirilmiş, ancak makale tablolarında gösterilen en küçük model gemma2:9b | TR-MMLU (6.200 soru, 62 bölüm, TUS dahil) | TUS: GPT-4o %91, Claude-3.5 Sonnet %88. **≤4B modellerin TUS sonucu makalede görülmedi → DOĞRULANMADI** |
| Design and Evaluation of a Source-Grounded Medical LLM for Clinical Decision Support and Patient Care in Trustworthy Diagnostic Systems | Muhammad Jamil, Adnan Kavak, Sevinç İlhan Omurca, Hossein Fotouhi | 2026 (Diagnostics 16(19):3142) | [10.3390/diagnostics16193142](https://doi.org/10.3390/diagnostics16193142) · [GitHub](https://github.com/Jamil226/TurkishMedLLM) | Qwen3-8B (QLoRA) + RAG | 210.791 Türkçe tıbbi soru-cevap çifti (SFT); 22.135 hastane makalesi (RAG) | Retrieval hit@1 %94,67; ROUGE-1/L 0,8338/0,7836; RAGAS faithfulness 0,91. Bilgiler GitHub README'den; dergi sayfası açılmadı (403) |
| Healthcare-Focused Turkish Medical LLM: Training on Real Patient-Doctor Question-Answer Data for Enhanced Medical Insight | **DOĞRULANMADI** (ACM sayfası açılmadı, 403) | 2025 (ACM TALLIP) | [10.1145/3772000](https://doi.org/10.1145/3772000) | LLaMA 3 (8B), LoRA | 167.732 hasta-doktor soru-cevap çifti (arama özetinden) | Uzman puanı 2,59 (taban model 2,00). Arama özetinden → **DOĞRULANMADI** |
| Do LLMs Provide Consistent Answers to Health-Related Questions across Languages? | Ipek Baris Schlicht, Zhixue Zhao, Burcu Sayin, Lucie Flek, Paolo Rosso | 2025 (ECIR 2025) | [arXiv:2501.14719](https://arxiv.org/abs/2501.14719) | ChatGPT, GPT-4o, Llama3-70B, Command R+ | Genişletilmiş HealthFC (Türkçe çevirili) | Türkçe ortalama tutarsızlık: ChatGPT %47,34, GPT-4o %48,26, Llama3 %67,61, Command R+ %68,12 |
| Zoom In Disparities in Healthcare LLM Q&A | Ipek Baris Schlicht, Burcu Sayin, Zhixue Zhao, vd. | 2025/2026 (NLDB 2026) | [arXiv:2510.17476](https://arxiv.org/abs/2510.17476) | Llama 3.3 70B, Qwen3-Next-80B-A3B, Aya Expanse 32B | MultiWikiHealthCare | Türkçe sorularda cevaplar İngilizce Vikipedi ile daha uyumlu (ör. Llama: Türkçe kanıtla 27,44, İngilizce kanıtla 30,89) |

## Projeyi doğrudan ilgilendiren veri seti bulguları

| Veri seti | Bağlantı | Satır sayısı | Lisans | Erişim | Not |
|---|---|---|---|---|---|
| MedTurkQuAD | [incidelen/MedTurkQuAD](https://huggingface.co/datasets/incidelen/MedTurkQuAD) | 8.200 (eğitim 6.560, doğrulama 820, test 820) | **CC-BY-NC-ND-4.0** | Kapılı olduğu belirtilmemiş | Kartta atıf bilgisi yok; makale DOI'si model kartından (10.1109/IDAP64064.2024.10711128) |
| Turkish MMLU (Bayram) | [alibayram/turkish_mmlu](https://huggingface.co/datasets/alibayram/turkish_mmlu) | 293.468 soru, 67 bölüm (TUS dahil; TUS soru sayısı kartta yok → **DOĞRULANMADI**) | **CC BY-NC-ND 4.0** | Kapılı (giriş gerekiyor) | Atıf: Zenodo [10.5281/zenodo.13378019](https://doi.org/10.5281/zenodo.13378019) |

**Uyarı:** `docs/02-model-secim-kriterleri.md` içindeki iki değerlendirme veri seti de **NoDerivatives (ND)**
lisanslı. Bu veri setlerini değerlendirmede kullanmanın sorun olmayacağını, ancak üzerlerinde **fine-tune** yapmanın
veya değiştirip yeniden dağıtmanın ND koşulunu ihlal edebileceğini **tahmin** ediyorum. Bu hukuki bir yorum değil;
lisans metni okunmalı ve danışmana sorulmalı.

## Doğrulanması gerekenler

- [ ] İncidelen ve Aydoğan (2024): IEEE Xplore'daki özetten EM 55,121 / F1 77,187 değerlerini ve hangi BERTurk türevlerinin karşılaştırıldığını kontrol et.
- [ ] TR-MMLU (arXiv:2501.00593): 39 modelin tam listesinde ≤4B model var mı, TUS puanları nerede (ek, GitHub ya da leaderboard)?
- [ ] ACM TALLIP 10.1145/3772000: yazarlar, taban model boyutu ve 2,59 puanı makaleden kontrol et.
- [ ] Diagnostics 10.3390/diagnostics16193142: yayının varlığını ve README'deki sayıları dergi sayfasından kontrol et.
- [ ] hoatac/gemma-3n-E2B-Turkish-Medical-QA: kartta yazan Apache-2.0 lisansı taban modelin (Gemma 3n) lisansıyla uyumlu mu?
- [ ] hoatac/Kumru-...-2B: taban modeli ve eğitim verisi ("Mutlu-5K" ne?) belirlenebilir mi?
- [ ] MedTurkQuAD ve turkish_mmlu için CC BY-NC-ND 4.0 lisansının değerlendirme ve fine-tune kullanımına etkisi (danışmana sor).
- [ ] turkish_mmlu içindeki TUS sorusu sayısı ve dahiliye alt kümesinin nasıl ayrılacağı.
- [ ] KSÜ Mühendislik Bilimleri Dergisi 28(2) 2025, "Türkçe sağlık danışmanlığında büyük dil modellerinin hasta-doktor iletişiminde kullanım potansiyeli" ([bağlantı](http://jes.ksu.edu.tr/tr/pub/article/1613938)): sayfa açılmadı. Arama özetine göre 7–8B modeller kullanılmış (kapsam dışı); yazarlar ve DOI **DOĞRULANMADI**, bu yüzden tabloya alınmadı.
- [ ] Google Scholar, DergiPark ve YÖK Tez Merkezi'nde "TUS" + "dil modeli" ve "Türkçe tıbbi soru cevap" aramalarını elle tekrarla. Bu tarama tezleri kapsamıyor.

## Kaynaklar

- İncidelen ve Aydoğan 2024: https://doi.org/10.1109/IDAP64064.2024.10711128 · https://ieeexplore.ieee.org/document/10711128/
- MedTurkQuAD: https://huggingface.co/datasets/incidelen/MedTurkQuAD
- MedBERTurkQA 128k: https://huggingface.co/incidelen/bert-base-turkish-128k-cased-medical-qa
- kaixkhazaki/turkish-medical-question-answering: https://huggingface.co/kaixkhazaki/turkish-medical-question-answering
- hoatac/gemma-3n-E2B-Turkish-Medical-QA: https://huggingface.co/hoatac/gemma-3n-E2B-Turkish-Medical-QA
- hoatac/gemma-3n-Turkish-Medical-QA-Merged: https://huggingface.co/hoatac/gemma-3n-Turkish-Medical-QA-Merged
- hoatac/Kumru-Turkish-Medical-2B-QA-4bit-Mutlu-5K: https://huggingface.co/hoatac/Kumru-Turkish-Medical-2B-QA-4bit-Mutlu-5K
- cuneytkaya/fine-tuned-t5-small-turkish-mmlu: https://huggingface.co/cuneytkaya/fine-tuned-t5-small-turkish-mmlu
- Turkish MMLU veri seti: https://huggingface.co/datasets/alibayram/turkish_mmlu · https://doi.org/10.5281/zenodo.13378019
- Hugging Face model araması ("turkish-medical"): https://huggingface.co/api/models?search=turkish-medical
- Koçak, Oğuz, Akçalı 2025: https://pmc.ncbi.nlm.nih.gov/articles/PMC12023555/
- Aygül, Olucoğlu, Alpkoçak 2024: https://arxiv.org/abs/2408.12305
- TR-MMLU: https://arxiv.org/abs/2501.00593
- TurkishMedLLM: https://github.com/Jamil226/TurkishMedLLM
- ACM TALLIP: https://dl.acm.org/doi/10.1145/3772000
- Schlicht vd. 2025: https://arxiv.org/abs/2501.14719
- Schlicht vd. 2025/2026: https://arxiv.org/abs/2510.17476
- Tıbbi olmadığı için elenen çalışmalar: RAGTurk (SIGTURK 2026, https://aclanthology.org/2026.sigturk-1.15.pdf), Arzu ve Aydoğan 2025 (https://doi.org/10.17694/bajece.1576976, genel Türkçe QA), TurkBench (arXiv:2601.07020), Cetvel (arXiv:2508.16431), TurkishMMLU (arXiv:2407.12402, lise müfredatı; sağlık dersi yok), ECHO (arXiv:2608.06110; GPT-5 Mini ve Llama 3.3 70B).
