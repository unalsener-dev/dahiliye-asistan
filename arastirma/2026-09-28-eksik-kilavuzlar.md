# Eksik Kılavuzlar: Nefroloji, Gastroenteroloji, Romatoloji, Enfeksiyon Hastalıkları

- **Soru:** Nefroloji, gastroenteroloji, romatoloji ve enfeksiyon hastalıkları (KLİMİK) için Türk uzmanlık
  derneklerinin güncel Türkçe klinik kılavuzları hangileri? Her biri için dernek, kılavuz adı, yıl, doğrudan PDF
  bağlantısı ve kullanım/telif koşulu nedir?
- **Tarih:** 2026-09-28
- **Araç:** Claude (Claude Code; WebSearch, WebFetch, `curl` ile indirme, `pdftotext` ile metin çıkarma)

## Yöntem

- Tabloya yalnızca **bağlantısı açılan** (HTTP 200, `application/pdf`) ve **indirilip içi okunan** PDF'ler alındı.
- **Yıl** PDF'in kapak veya künye sayfasından okundu. PDF'te okunamadığında kaynağı ayrıca belirtildi.
- **Telif/kullanım koşulu** önce PDF'in içinden, yoksa dernek sayfasının altbilgisinden aynen aktarıldı. Hangi
  kaynaktan geldiği her satırda yazıyor.
- **Not:** `pdftotext` bazı PDF'lerde Türkçe karakterleri (İ, ğ, ş) düşürdü. Alıntılarda bu karakterler elle
  düzeltildi; anlam değiştirilmedi. Bu sorun `ingest/` hattını da ilgilendiriyor (aşağıdaki "Pratik notlar"
  bölümüne bakın).

## 1. Nefroloji — Türk Nefroloji Derneği (TND)

Liste sayfası: https://nefroloji.org.tr/tr/kilavuz-ve-kitaplar · Site altbilgisi: **"Tüm Hakları Saklıdır | Türk Nefroloji Derneği"**

| Kılavuz | Yıl | PDF | Kullanım / telif koşulu |
|---|---|---|---|
| Hiperpotasemisi Olan Hastanın Yönetimi – TND Uzman Görüşü Raporu | Ocak 2026 (kapak) | https://nefroloji.org.tr/uploads/files/hiperpotasemisi.pdf | PDF'te telif cümlesi bulunamadı → site altbilgisi geçerli: "Tüm Hakları Saklıdır" |
| Diyabeti Olan Kronik Böbrek Hastalarında Hiperglisemi Yönetimi – TND Uzman Görüşü Raporu 2025 | Ekim 2025 (künye) | https://nefroloji.org.tr/uploads/pdf/uzman_gorusu_raporu.pdf | PDF'te telif cümlesi bulunamadı → site altbilgisi |
| Türk Hipertansiyon Uzlaşı Raporu 2025 (TKD, THUD, TEMD, TND, THBHD, TAHUD, AGD ortak) | 2025 (kapak) | https://nefroloji.org.tr/uploads/files/uzlasi-raporu.pdf | PDF'te telif cümlesi bulunamadı → site altbilgisi |
| Asit-Baz Bozukluklarına Yaklaşım ve Kronik Metabolik Asidoz Yönetimi – TND Uzlaşı Raporu 2023 | Kasım 2023 (künye) | https://nefroloji.org.tr/uploads/pdf/TND-uzlasi-raporu.pdf | PDF'te telif cümlesi bulunamadı → site altbilgisi |
| RAAS İnhibitörü Başlanan Kronik Böbrek Hastasında Hiperpotasemi Yönetimi (2 sayfalık algoritma) | **Bilinmiyor** (PDF'te yıl yok) | https://nefroloji.org.tr/uploads/files/RAASi.pdf | Site altbilgisi |
| KDIGO 2021 Glomerüler Hastalıkların Yönetimi İçin Klinik Uygulama Kılavuzu (Türkçe çeviri, özet) | 2021 kılavuzunun çevirisi; çeviri yılı PDF'te **bilinmiyor** | https://nefroloji.org.tr/uploads/pdf/KDIGO-TND.pdf | PDF'te derneğe ait telif cümlesi yok. Şekillerde "... izniyle" ibareleri var. Özgün eser KDIGO'ya ait; çeviri hakkı **DOĞRULANMADI** |
| Primer Glomerüler Hastalıkların Tanı ve Tedavisi: TND Ulusal Uzlaşı Raporu | Basım tarihi 16.09.2019 | https://nefroloji.org.tr/uploads/folders/file/Primer_Glomeruler_Hastaliklarin_Tani_ve_Tedavisi.pdf | PDF künyesi: **"Bu kitabın içeriğinin tümü veya bir bölümü Türk Nefroloji Derneği'nin yazılı izni olmadıkça kullanılamaz. Ancak kaynak gösterilerek alıntı yapılabilir. Sözlü ya da yazılı olarak veya daha başka bir yöntemle çoğaltılamaz ya da yayınlanamaz."** |

**Açıldı ama tabloya alınmadı:**
- ISPD Peritonit (2022) ve ISPD Kateter İlişkili Enfeksiyon (2023) çevirileri: periton diyaliziyle ilgili;
  intörn dahiliye kapsamı için öncelikli değil. Her iki bağlantı da çalışıyor.
- "Hızlı İlerleyici ODPBH Yönetimi" bağlantısı **404** veriyor.
- "KBH Anemisinin ESA ile Tedavi İlkeleri" bağlantısı (`buffer?gid=107`) PDF değil, boş sayfa döndü.

## 2. Gastroenteroloji

### 2a. Türk Gastroenteroloji Derneği (TGD) — kılavuz bulunamadı

- https://tgd.org.tr/ sitesinde "kılavuz / rehber / uzlaşı" başlıklı bir bölüm **bulunamadı**. Menüde yalnızca
  kurumsal kimlik rehberi ve yönergeler var. Site altbilgisi: **"© Copyright 1959-2026 TGD"**.
- Arama sonuçlarında TGD'nin Türkçe, güncel ve PDF'i açılabilen bir klinik kılavuzu **doğrulanamadı**.
  Arama motoru özetinde 2017 tarihli bir GÖRH uzlaşı raporundan söz ediliyor, ancak bağlantısı açılmadı. Bu yüzden
  tabloya **alınmadı**.
- Güncel Gastroenteroloji (TGV) dergisindeki yazılar derleme niteliğinde; dernek kılavuzu olmadıkları için
  alınmadı.

### 2b. Gastroenteroloji yan dalındaki diğer dernekler

TGD olmasa da gastroenteroloji/hepatoloji kapsamında Türkçe PDF'i doğrulanan kılavuzlar:

| Dernek | Kılavuz | Yıl | PDF | Kullanım / telif koşulu |
|---|---|---|---|---|
| İnflamatuvar Barsak Hastalıkları Derneği (İBHD) | İnflamatuvar Bağırsak Hastalıklarında Tanı ve Tedavi Uzman Görüş Raporu 2024 | "1. Baskı Mayıs 2024" (künye) | https://ibhd.org.tr/dosya/Uzman_Gorus_Raporu_30122024.pdf | PDF künyesi: **"İnflamatuvar Bağırsak Hastalıkları Uzman Görüş Raporu, İnflamatuvar Barsak Hastalıkları Derneği'nin yayınıdır. Tüm hakları saklıdır. Türkiye'deki dağıtım hakkı ve yetkisi sadece İnflamatuvar Barsak Hastalıkları Derneği'ne aittir. Önceden İnflamatuvar Barsak Hastalıkları Derneği'nin yazılı izni olmaksızın kopyalanamaz, çoğaltılamaz ve tanıtım amaçlı bile olsa alıntı yapılamaz."** |
| Türk Karaciğer Araştırmaları Derneği (TKAD) + Viral Hepatitle Savaşım Derneği (VHSD) | Türkiye Hepatit B Tanı ve Tedavi Kılavuzu 2023 | 2023 (kapak) | https://www.tkad.org.tr/wp-content/uploads/2023/11/TURKIYE-HEPATIT-B-TANI-VE-TEDAVI-KLAVUZU-2023.pdf | PDF'te telif cümlesi yok → site altbilgisi: **"©2023 TKAD, Tüm Hakları Saklıdır"** |
| TKAD + VHSD | Türkiye Hepatit C Tanı ve Tedavi Kılavuzu 2023 | 2023 (kapak) | https://www.tkad.org.tr/wp-content/uploads/2023/11/TURKIYE-HEPATIT-C-TANI-VE-TEDAVI-KLAVUZU-2023.pdf | Aynı (site altbilgisi) |

**Not:** TKAD'ın kılavuz sayfasında (https://www.tkad.org.tr/tkad-kilavuzlar/) 20'den fazla başka başlık var
(karaciğer nakli, HCC vb.). Bunların PDF bağlantıları açılmadığı için tabloya alınmadı.

## 3. Romatoloji — Türkiye Romatoloji Derneği (TRD)

Liste sayfası: https://www.romatoloji.org/OgrenmeMerkezi/HekimlerIcin/TRDUlusalTedaviOnerileri · Site altbilgisi: **"Türkiye Romatoloji Derneği Tüm Hakları Saklıdır ©2018"**

| Kılavuz | Yıl | PDF | Kullanım / telif koşulu |
|---|---|---|---|
| Türkiye Romatoloji Derneği ANCA ilişkili (asosiye) vaskülitler hastalık yönetimi kılavuzu (DOI 10.4274/raed.galenos.2025.26349) | 2025 (Epub 01.09.2025) | https://www.raeddergisi.org/pdf/ecbfe058-16b4-48ee-945f-aeecbad1b86a/articles/raed.galenos.2025.26349/1-2025.26349.pdf | PDF: **"Copyright© 2025 Yazar. Türk Romatoloji Derneği adına Galenos Yayınevi tarafından yayımlanmıştır. Creative Commons Atıf-GayriTicari-Türetilemez 4.0 (CC BY-NC-ND) Uluslararası Lisansı ile lisanslanmış, açık erişimli bir makaledir."** |
| TRD romatoid artrit ulusal tedavi önerileri (doi:10.2399/raed.18.18022) | 2018 | https://www.romatoloji.org/Dokumanlar/TRDUlusalTedaviOnerileri/URD_2018002002.pdf | PDF: **"© 2018 TRD"** (ayrıca bir kullanım cümlesi yok) + site altbilgisi |
| TRD aksiyel spondiloartrit ulusal tedavi önerileri (doi:10.2399/raed.18.18024) | 2018 | https://www.romatoloji.org/Dokumanlar/TRDUlusalTedaviOnerileri/URD_2018002004.pdf | PDF: **"© 2018 TRD"** |
| TRD psoriyatik artrit ulusal tedavi önerileri (doi:10.2399/raed.18.18021) | 2018 | https://www.romatoloji.org/Dokumanlar/TRDUlusalTedaviOnerileri/URD_2018002001.pdf | PDF: **"© 2018 TRD"** |

**Not:** TRD'nin ulusal tedavi önerileri 2018 tarihli; "güncel" sayılıp sayılmayacağına danışmanla karar verilmeli.
Sayfadaki "Biyobenzerler" (2018) belgesinin PDF'i açılıyor ancak klinik yönetim kılavuzu olmadığı için alınmadı.

## 4. Enfeksiyon Hastalıkları — KLİMİK

Site altbilgisi (klimik.org.tr): **"2026 © Bu sitenin tüm hakları KLİMİK Derneğine aittir."** Sitede ayrı bir
"Kılavuzlar" menüsü yok. Kılavuzlar Klimik Dergisi'nde ve "KLİMİK Kitapları" sayfasında yayımlanıyor.

| Kılavuz | Yıl | PDF | Kullanım / telif koşulu |
|---|---|---|---|
| KLİMİK Kanıta Dayalı Bruselloz Tanı ve Tedavi Klinik Uygulama Rehberi, 2023 (Klimik Derg 36(2):86-123, DOI 10.36519/kd.2023.4576) | 2023 | https://www.klimikdergisi.org/en/download-pdf/?id=31983 | PDF: **"Bu çalışma Creative Commons Atıf-GayriTicari-Türetilemez 4.0 Uluslararası Lisansı ile lisanslanmıştır."** ⚠️ Dergi web sayfası ise **"CC BY-NC 4.0"** diyor; iki kaynak **çelişiyor** |
| Diyabetik Ayak Yarası ve İnfeksiyonunun Tanısı, Tedavisi, Önlenmesi ve Rehabilitasyonu: Ulusal Uzlaşı Raporu, 2024 (Klimik Derg 37(1):1-43, DOI 10.36519/kd.2024.4822; çok dernekli, KLİMİK öncülüğünde) | 2024 | https://www.klimikdergisi.org/en/download-pdf/?id=28612 | PDF: **"Bu çalışma Creative Commons Atıf-GayriTicari-Türetilemez 4.0 Uluslararası Lisansı ile lisanslanmıştır."** ⚠️ Web sayfası **"CC BY-NC 4.0"** diyor; çelişki |
| HIV/AIDS Tanı, İzlem ve Tedavi El Kitabı Sürüm 4.0 (Editörler: Gökengin, Korten, Kurtaran, Tabak, Ünal) | 2026 (KLİMİK kitap listesi; PDF'teki yıl metni bozuk okundu) | https://www.klimik.org.tr/wp-content/uploads/2026/08/978-625-8984-28-6-HIV_AIDS-Tani-Izlem-ve-Tedavi-El-Kitabi-Surum-4.0-1.pdf | PDF: **"Bu kitabın, 5846 ve 2936 sayılı Fikir ve Sanat Eserleri Yasası Hükümleri gereğince editörün yazılı izni olmadan bir bölümünden alıntı yapılamaz; fotokopi yöntemiyle çoğaltılamaz; resim, şekil, şema, grafik vb.ler kopya edilemez. Her hakkı Nobel Tıp Kitabevleri Ltd. Şti'ne aittir."** Yayıncı Nobel Tıp; KLİMİK sitesinde barındırılıyor |
| Temas Öncesi Profilaksi Kılavuzu | Haziran 2022 (kapak) | https://www.klimik.org.tr/wp-content/uploads/2022/08/Temas.O%CC%88ncesi.Profilaksi.Kilavuzu_26.07.2022.pdf | PDF: "Bu kılavuz Türkiye HIV/AIDS Platformu'nun bir yayınıdır." Kullanım koşulu cümlesi yok → KLİMİK site altbilgisi |

**Not:** KLİMİK dahiliye intörnü için sık konularda (toplum kökenli pnömoni, üriner sistem infeksiyonu, sepsis)
güncel bir Türkçe KLİMİK kılavuzu bu taramada **bulunamadı**. Bu konuların Klimik Dergisi arşivinde ayrıca
aranması gerekiyor.

## Özet: Lisans açısından RAG'e uygunluk (yorum, hukuki görüş değil)

| Durum | Belgeler |
|---|---|
| Açık lisanslı (CC BY-NC-ND / CC BY-NC): ticari olmayan kullanım serbest, türev koşulu belirsiz | TRD ANCA 2025; KLİMİK Bruselloz 2023; KLİMİK Diyabetik Ayak 2024 |
| "Kaynak gösterilerek alıntı yapılabilir" açık izni var | TND Primer Glomerüler Hastalıklar (2019) |
| Yazılı izin olmadan alıntı bile açıkça **yasak** | İBHD 2024; HIV/AIDS El Kitabı 4.0 |
| Yalnızca "Tüm hakları saklıdır" (site altbilgisi) | TND 2023–2026 raporları; TKAD 2023; TRD 2018 önerileri; KLİMİK Temas Öncesi Profilaksi |

Bir kılavuzu yerel vektör veritabanına alıp kısa parçalarını kaynak göstererek göstermenin "alıntı" sayılacağını
**tahmin** ediyorum. Ama **İBHD ve HIV El Kitabı açıkça "alıntı yapılamaz" diyor**. Bu iki belge için dernekten
yazılı izin alınmadan sisteme eklenmemesini öneririm. Diğerleri için de danışmanla birlikte derneklere izin
e-postası göndermek en güvenli yol.

## Pratik notlar (ingest için)

- `pdftotext` ile çıkarılan metinde birçok PDF'te **Türkçe karakterler düştü** (ör. "Türk Nefroloji Derneği" →
  "T�rk Nefroloji Dernei"). Bu durum TND, İBHD, TKAD ve KLİMİK PDF'lerinin tümünde görüldü. PyMuPDF'in bu
  PDF'lerde doğru çıktı verip vermediği test edilmeli; bozuk metin embedding kalitesini düşürür.
- İki sütunlu dergi PDF'lerinde (Klimik Dergisi, Ulusal Romatoloji Dergisi) satırlar sütunlar arasında
  karışıyor; parçalama öncesinde sütun ayrımı gerekir.

## Doğrulanması gerekenler

- [ ] KLİMİK Bruselloz 2023 ve Diyabetik Ayak 2024: lisans **CC BY-NC-ND 4.0 mı (PDF), CC BY-NC 4.0 mı (web sayfası)?** Klimik Dergisi'ne sor ya da dergi politikası sayfasına bak.
- [ ] TND: RAASi algoritmasının yılı; KDIGO 2021 çevirisinin yılı ve çeviri/yayın izni.
- [ ] TND "Hızlı İlerleyici ODPBH" raporunun güncel bağlantısı (mevcut bağlantı 404).
- [ ] TGD'nin Türkçe güncel bir kılavuzu gerçekten yok mu? Dernekle iletişime geç (site: tgd.org.tr). 2017 GÖRH uzlaşı raporunun tam metnini bul.
- [ ] TKAD sayfasındaki diğer kılavuzların (siroz komplikasyonları, HCC vb.) PDF bağlantıları.
- [ ] TRD'nin 2018 sonrası güncellenmiş RA/SpA/PsA önerileri var mı? Ayrıca "gebelik ve laktasyon önerileri" (doi:10.2399/raed.19.61061) PDF'i açılmadı.
- [ ] Türkiye Romatizma Araştırma ve Savaş Derneği'nin (TRASD) "Tanı ve Tedavi Rehberleri" sayfası (https://trasdonline.org/tani-ve-tedavi-rehberleri) açılmadı; romatoloji için ikinci bir kaynak olabilir.
- [ ] KLİMİK: pnömoni, idrar yolu infeksiyonu, sepsis, febril nötropeni konularında güncel Türkçe rehber var mı (Klimik Dergisi arşivi)?
- [ ] HIV El Kitabı 4.0'ın yayın yılı (PDF'te "2026" mı?).
- [ ] Her belge için ilgili derneğe kullanım izni e-postası (danışmanla birlikte).
