# Panduan Sistematis Penelusuran, Screening, Pengorganisasian, dan Penulisan Literatur untuk Tugas Akhir

---

## 1. Formula Pencarian Literatur Tersistematis

### A. Rekomendasi Kata Kunci (Keywords)
Berikut adalah kata kunci berbasis bahasa Inggris yang dikelompokkan berdasarkan domain dan topik penelitian:

1. **Domain & Problem Context:**
   - `"imbalanced data"`
   - `"class imbalance"`
   - `"extreme class imbalance"`
   - `"minority class"`
   - `"time-series telemetry"`

2. **Domain Application:**
   - `"IoT sensor data"`
   - `"hydroponics"`
   - `"smart agriculture"`
   - `"precision agriculture"`
   - `"actuator control"`

3. **Methodology & Model:**
   - `"SMOTE-Tomek"`
   - `"hybrid resampling"`
   - `"Random Forest"`
   - `"cost-sensitive learning"`
   - `"data cleaning"`

---

### B. Rekomendasi Strategi Pencarian Operator Boolean
Kombinasikan kata kunci menggunakan logika `AND`, `OR`, `NOT`, serta tanda kutip `""` untuk frasa persis dan tanda bintang `*` untuk variasi kata (*truncation*):

- **String 1:**
  ```text
  (("imbalanced data" OR "class imbalance")  AND ("IoT" OR "time-series") AND ("smart agriculture" OR "hydroponic*")) AND (("SMOTE-Tomek" OR "hybrid resampling") AND ("SMOTE" OR "Tomek links")) AND ("F1-Score" OR "MCC")
  ```
- **String 2:**
  ```text
  (("smart agriculture" OR "hydroponics" OR "precision agriculture") AND (("IoT" OR "Internet of Things" OR "telemetry") AND "binary class") AND ("Overlap*") AND ("imbalanced data" OR "class imbalance" OR "extreme class imbalance")) AND ("SMOTE" OR "Tomek links" OR "SMOTE-Tomek" OR "hybrid resampling") AND ("Random Forest" OR "SVM" OR "KNN" OR "machine learning*") AND ("Recall" OR "Precision" OR "F1-Score" OR "AUC-PR")
  ```
- **String 2:**
  ```text
  (("smart irrigation system" OR "hydroponics") AND (("IoT" OR "Internet of Things" OR "telemetry") AND "binary class") AND ("Overlap*") AND ("imbalanced data" OR "class imbalance" OR "extreme class imbalance")) AND ("SMOTE" OR "Tomek links" OR "SMOTE-Tomek" OR "hybrid resampling") AND ("Random Forest" OR "machine learning*") AND ("Recall" OR "Precision" OR "F1-Score" OR "AUC-PR" OR "MCC")
  ```

### C. Rekomendasi Database Open Access \& Kredibel
1. Google Scholar (Cakupan luas, gunakan filter tahun 2020–2026).
2. IEEE Xplore Open Access (Sangat kuat untuk domain IoT, teknik elektro, dan informatika).
3. ScienceDirect / Elsevier (Open Access Filter) (Jurnal bereputasi tinggi bidang pertanian presisi dan sains data).
4. DOAJ (Directory of Open Access Journals) (Direktori jurnal full open access peer-reviewed).
5. ResearchGate & arXiv (Untuk mencari pre-print atau draf penulis jika jurnal utama terkunci paywall).

### D. Strategi Backward Chaining \& Forward Chaining + Tools
1. Backward Chaining (Melihat ke Belakang):
    * Teknik: Ambil 2–3 jurnal utama (anchor papers), lalu periksa daftar pustaka (references) jurnal tersebut untuk menemukan penelitian dasar/pionir.
2. Forward Chaining (Melihat ke Depan):
    * Teknik: Gunakan fitur "Cited by" di Google Scholar atau Scopus untuk menemukan penelitian terbaru yang mengutip jurnal dasar tersebut.
3. Tools Pendukung:
    * Connected Papers / ResearchRabbit: Masukkan DOI dari jurnal utama Anda untuk melihat peta visual keterhubungan antar-makalah.
    * Zotero / Mendeley: Untuk mengorganisasi repositori sitasi dan file PDF secara otomatis.

### E. Strategi Tambahan: PICO\/PECO Framework \& Filter Mutu
* PICO Framework untuk Pencarian:
    * P (Population/Problem): Imbalanced time-series IoT sensor data in hydroponics.
    * I (Intervention/Method): SMOTE-Tomek resampling with Random Forest.
    * C (Comparison): Baseline model (unbalanced raw data) or single resampling techniques (RUS/SMOTE).
    * O (Outcome): Recall, Precision, F1-Score, AUC-PR.

* Grey Literature Check: Periksa repositori perguruan tinggi atau skripsi/tesis luar negeri untuk melihat rincian eksperimen teknis yang sering kali tidak dimuat secara detail di jurnal pendek.

## 2. Formula Teknik Screening Literatur
### A. Kriteria Inklusi dan Eksklusi
| Kategori | Kriteria Inklusi (Diterima) | Kriteria Eksklusi (Ditolak) |
| :--- | :--- | :--- |
| **Rentang Waktu** | Dipublikasikan dalam kurun waktu 2020–2026. | Dipublikasikan sebelum tahun 2020 (kecuali jurnal pionir algoritma SMOTE/Tomek). |
| **Topik Utama** | Membahas *imbalanced data*, *resampling* (SMOTE/SMOTE-Tomek), *Random Forest*, atau klasifikasi data sensor/IoT. | Hanya membahas pemeliharaan fisik tanaman tanpa melibatkan *machine learning* atau pemodelan data. |
| **Jenis Dokumen** | Artikel jurnal ilmiah peer-reviewed dan *conference proceedings* bergengsi. | Artikel blog, opini pribadi, editorial non-peer reviewed, atau presentasi slide. |
| **Bahasa** | Bahasa Indonesia atau Bahasa Inggris. | Bahasa selain Indonesia dan Inggris. |
| **Aksesibilitas** | Teks lengkap (*full-text*) dapat diakses dan dibaca. | Hanya tersedia abstrak tanpa akses *full-text*. |

### B. Penilaian Kredibilitas (Quality Assessment)
Periksa kredibilitas jurnal sebelum digunakan sebagai rujukan utama:
1. Penerbit Bereputasi: Terindeks oleh Scopus (Q1–Q4), DOAJ, SINTA (S1–S3), IEEE, Elsevier, Springer, atau MDPI.
2. Metodologi Jelas: Artikel mencantumkan detail dataset, perlakuan pre-processing, serta metrik evaluasi secara komprehensif.
3. Reproduosibilitas: Menyediakan informasi algoritma/parameter yang cukup untuk diuji ulang.

### C. Systematic Prompt untuk Screening menggunakan NotebookLM
Systematic Prompt (Screening Literatur):
```text
"You are a rigorous academic researcher assisting in a systematic literature screening process for an undergraduate thesis on imbalanced time-series data classification for IoT hydroponic sensors using SMOTE-Tomek and Random Forest.

Read the uploaded documents carefully and evaluate their relevance against the following Inclusion and Exclusion criteria:

Inclusion Criteria:
1. Focuses on machine learning for time-series, IoT sensor data, or smart agriculture.
2. Discusses class imbalance handling (e.g., SMOTE, SMOTE-Tomek, undersampling, oversampling, or cost-sensitive learning).
3. Evaluates classification models using metrics like Recall, Precision, Accuracy, F1-Score, or AUC-PR.

Exclusion Criteria:
1. Non-peer-reviewed articles, opinion pieces, or incomplete full-texts.
2. Studies purely focused on agricultural biology without any data modeling or algorithmic analysis.

Task:
Provide the output IN INDONESIAN using the following structured layout for EACH uploaded document:

1. Judul Artikel & Penulis (Tahun):
2. Status Screening: [DITERIMA / DITOLAK / DIRAGUKAN]
3. Alasan Keputusan (Sebutkan poin kriteria inklusi/eksklusi yang terpenuhi atau dilanggar):
4. Ringkasan Singkat Kontribusi: (Maksimal 3 kalimat tentang temuan utama yang relevan dengan topik kita)."
```

## 3. Pengolahan & Pengorganisasian Data dengan Matriks Sintesis
### A. Format Matriks Sintesis Literatur
| No | Penulis (tahun) | Fokus Penelitian/Masalah | Dataset & Domain | Metode / Algoritma | Metrik Evaluasi | Hasil & Temuan | Keterbatasan / Research Gap |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Hasil | Hasil | Hasil | Hasil | Hasil | Hasil | Hasil | Hasil |

### B. Systematic Prompt Ekstraksi Matriks Sintesis untuk NotebookLM
Systematic Prompt (Ekstraksi Matriks Sintesis):
```text
"You are an expert literature reviewer. Analyze all accepted documents uploaded in this notebook and extract the core information to populate a Literature Synthesis Matrix.

Task:
Generate a structured Markdown table IN INDONESIAN with the following columns:
1. Penulis & Tahun
2. Masalah Utama yang Diteliti
3. Dataset & Domain (e.g., IoT, time-series, sensor)
4. Metode / Algoritma yang Digunakan (e.g., SMOTE, Random Forest, Cost-Sensitive)
5. Metrik Evaluasi (e.g., F1-Score, Recall, Accuracy)
6. Temuan Utama / Kinerja Model
7. Keterbatasan Penelitian / Research Gap
8. Relevansi Spesifik dengan Penelitian SMOTE-Tomek + Random Forest untuk Aktuator Hidroponik

Ensure the information extracted is strictly factual and directly derived from the uploaded sources without speculation."
```

