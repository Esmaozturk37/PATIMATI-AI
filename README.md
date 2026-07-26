# 🐾 PatiMati - AI Core Module

![PatiMati Banner](https://img.shields.io/badge/PatiMati-AI%20Core-orange?style=for-the-badge&logo=python)
![Python Version](https://img.shields.io/badge/python-3.10%2B-blue?style=for-the-badge&logo=python)
![Status](https://img.shields.io/badge/Status-In%20Development-green?style=for-the-badge)

**PatiMati AI Core**, kayıp ve sahipsiz evcil hayvan ilanlarını görsel analiz (Computer Vision) ve doğal dil işleme (NLP) teknikleriyle otomatik olarak eşleştiren, doğrulayan ve değerlendiren yapay zekâ servislerinin ortak merkez deposudur.

---

## 🚀 Proje Hakkında

PatiMati; sosyal medyadan toplanan ilanlar ile kullanıcıların yüklediği fotoğrafları, öznitelikleri ve metin açıklamalarını analiz ederek kayıp hayvanların bulunma süresini en aza indirmeyi ve doğru eşleştirmeler sunmayı hedefler.

AI modülü, hem görseller üzerinden hem de ilan metinlerindeki anlamsal detaylar üzerinden çok boyutlu (multimodal) bir eşleştirme mimarisi sunar.

---

## 🧩 AI İş Paketleri (Work Packages)

AI ekibimiz, sistemin farklı bileşenlerini geliştirmek için 4 bağımsız iş paketi paralelinde çalışmaktadır:

### 📦 Paket 1: Veri Kümesi & Doğrulama (Dataset & Validation Tool)
- **Amaç:** Zorlu koşullardaki (bulanık, karanlık, açı farkı olan) ve aynı hayvanın farklı günlerde çekilmiş fotoğraflarını toplama ve etiketleme.
- **İçerik:** Bozuk dosya, eksik etiket ve tekrar eden fotoğraf kontrolü yapan otomatik doğrulama aracı.
- **Çıktı:** Doğrulanmış 150+ etiketli görsel veri seti ve doğrulama aracı.

### 📦 Paket 2: Değerlendirme Düzeneği (Evaluation Pipeline)
- **Amaç:** Mevcut eşleştirme modelinin dayanıklılık ve başarım sınırlarını ölçmek.
- **İçerik:** Fotoğrafları kademeli olarak bozarak (bulanıklaştırma, karartma, döndürme, sıkıştırma) modelin eşleştirme katsayısının nerede koptuğunu bulan test aracı.
- **Çıktı:** Otomatik test aracı ve sunumlarda kullanılacak olan dayanıklılık/başarım grafikleri.

### 📦 Paket 3: Öznitelik Geliştirme (Feature Engineering & Zero-Shot)
- **Amaç:** Görsel eşleştirme skoruna ek sinyaller kazandırmak.
- **İçerik:** Tasma, kulak küpesi, tüy uzunluğu, kulak biçimi, kuyruk ve boyut gibi spesifik özellikleri model uzayına ekleme ve skor katkısını ölçme. Aynı zamanda ilan formunu AI'ın otomatik doldurma özelliğini besler.
- **Çıktı:** Ölçümle kanıtlanmış öznitelik seti.

### 📦 Paket 4: İlan Metninden Eşleştirme (Text Matching & NLP)
- **Amaç:** Fotoğrafın gösteremediği (*"sol kulağı çentikli", "mavi tasmalı", "siyah tekir"*) bilgileri ilan metinlerinden çıkararak eşleştirmeye katmak.
- **İçerik:** İlan açıklamalarını vektörel gömme (text embedding) uzayına taşıyarak anlamsal benzerlik skorunu hesaplayan bağımsız modül.
- **Çıktı:** Metin benzerlik modülü ve başarım raporu.

---

## 📂 Proje Dizin Yapısı

```text
PATIMATI-AI/
├── data/                      # Gerçek ve çoğaltılmış test veri setleri (Paket 1)
│   ├── raw/                   # Ham fotoğraflar
│   └── processed/             # Etiketlenmiş ve doğrulanmış görseller
├── modules/
│   ├── dataset_validator/     # Veri doğrulama scripti ve etiketleme araçları (Paket 1)
│   ├── evaluation/            # Model dayanıklılık testi ve grafik üretici (Paket 2)
│   ├── feature_engineering/   # Öznitelik çıkarma ve zero-shot modülü (Paket 3)
│   └── text_matcher/          # İlan açıklamaları metin benzerlik modülü (Paket 4)
├── core/                      # Ana eşleştirme servisi ve model ağırlıkları
├── tests/                     # Her pakete özel birim (unit) testler
├── requirements.txt           # Bağımlılıklar
└── README.md                  # Proje ana dokümantasyonu