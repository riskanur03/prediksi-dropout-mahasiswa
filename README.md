# prediksi-dropout-mahasiswa
Studi Replikasi Prediksi Risiko Dropout dan Keberhasilan Akademik Berbasis Random Forest dan XGBoost.

# Prediksi Ganda Risiko Dropout dan Keberhasilan Akademik Mahasiswa: Studi Replikasi Berbasis Random Forest dan XGBoost

[![Python Version](https://img.shields.io/badge/python-3.9%20%7C%203.10-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Framework-Optuna-orange.svg)](https://optuna.org/)
[![Imbalance Method](https://img.shields.io/badge/Resampling-SMOTE-green.svg)](https://imbalance-learn.org/)

Repositori ini berisi kode implementasi dan dokumentasi lengkap untuk proyek eksperimen **Educational Data Mining (EDM)**. Proyek ini merupakan sebuah **Studi Replikasi** dari paper utama oleh *Villar & Andrade (2024)* untuk memprediksi tiga kelas luaran mahasiswa (*Dropout*, *Enrolled*, dan *Graduate*) menggunakan algoritma *Random Forest* (Bagging) dan *XGBoost* (Boosting).

---

## 📌 Fitur Utama Proyek
* **Penanganan Class Imbalance:** Mengintegrasikan teknik *Synthetic Minority Oversampling Technique* (SMOTE) secara ketat pada data pelatihan guna mencegah terjadinya kebocoran data (*data leakage*).
* **Automated Hyperparameter Tuning:** Memanfaatkan kerangka kerja (framework) **Optuna** berbasis *Bayesian Optimization* untuk mencari kombinasi parameter model paling optimal secara otomatis.
* **Evaluasi Multikelas Granular:** Melakukan analisis performa tidak hanya pada akurasi global, melainkan fokus pada metrik *Recall* dan *F1-Score* untuk mendeteksi kelas minoritas (*Dropout*).

---

## 📊 Dataset
Dataset yang digunakan dalam penelitian ini bersumber dari **UCI Machine Learning Repository**: *Predict Students Dropout and Academic Success* yang awalnya dibangun oleh *Martins dkk. (2021)* berdasarkan data institusional dari *Polytechnic Institute of Portalegre* (IPP), Portugal.

* **Jumlah Sampel Uji:** 885 observasi (Ekstraksi 20% data uji dari total dataset).
* **Proprietas Kelas Uji:** 284 sampel *Dropout*, 159 sampel *Enrolled*, dan 442 sampel *Graduate*.

---

## 📈 Hasil Eksperimen Berdasarkan Pengujian

Berdasarkan pengujian performa klasifikasi multikelas, kedua algoritma menghasilkan nilai Akurasi Global yang identik, yaitu sebesar **75,71%**. Namun, karakteristik performa pada masing-masing kelas target menunjukkan perbedaan yang signifikan:

### 1. Klasifikasi Model: Random Forest
* **Akurasi Global:** 75,71%
* **Performa per Kelas:**
  * `Dropout`: Precision: 0.84 | Recall: 0.69 | F1-Score: 0.75
  * `Enrolled`: Precision: 0.47 | Recall: 0.55 | F1-Score: 0.51
  * `Graduate`: Precision: 0.83 | Recall: 0.88 | F1-Score: 0.85

### 2. Klasifikasi Model: XGBoost
* **Akurasi Global:** 75,71%
* **Performa per Kelas:**
  * `Dropout`: Precision: 0.80 | **Recall: 0.72** | **F1-Score: 0.76**
  * `Enrolled`: Precision: 0.48 | Recall: 0.53 | F1-Score: 0.50
  * `Graduate`: Precision: 0.84 | Recall: 0.86 | F1-Score: 0.85

### 🔑 Temuan Utama & Validasi Paper Utama:
1. **Superioritas XGBoost pada Kelas Risiko:** Sejalan dengan klaim paper utama (*Villar & Andrade, 2024*), model berbasis *Boosting* (**XGBoost**) terbukti lebih unggul dalam mendeteksi kelas *Dropout* dengan nilai **Recall mencapai 72%** (dibandingkan Random Forest sebesar 69%).
2. **Keterbatasan Bersama (Shared Limitation):** Kedua model mengalami penurunan performa drastis pada kelas transisi (**Enrolled**) dengan *F1-Score* jatuh di kisaran **0.50 - 0.51**. Hal ini memvalidasi teori paper utama mengenai tingginya tingkat tumpang tindih data (*overlapping decision boundary*) pada transkrip tahun pertama mahasiswa aktif.

---

## 🛠️ Langkah Menjalankan Proyek (Setup)

### 1. Kloning Repositori
```bash
git clone [https://github.com/riskanur03/prediksi-dropout-mahasiswa](https://github.com/riskanur03/prediksi-dropout-mahasiswa)
cd riskanur03