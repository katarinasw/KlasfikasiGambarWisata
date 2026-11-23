# Klasifikasi Pemandangan & Rekomendasi Destinasi Wisata Indonesia
## Sistem Rekomendasi Waktu Terbaik Berkunjung Berbasis CNN

---

## Deskripsi Proyek
Proyek ini membangun model **Convolutional Neural Network (CNN)** menggunakan 
Transfer Learning MobileNetV2 untuk mengklasifikasikan jenis pemandangan dari 
sebuah foto ke dalam 4 kategori, sekaligus memberikan rekomendasi destinasi 
wisata Indonesia beserta waktu terbaik berkunjung berdasarkan musim.

---

## Kelas yang Diklasifikasikan
| No | Kelas | Deskripsi |
|----|-------|-----------|
| 1 | Forest | Hutan dan kawasan alam |
| 2 | Mountain | Gunung dan pegunungan |
| 3 | Sea | Pantai dan lautan |
| 4 | Street | Jalanan dan kawasan urban |

---

## Dataset
- **Nama Dataset:** Intel Image Classification
- **Sumber:** [Kaggle - puneet6060](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)
- **Jumlah Gambar:** ~25.000 gambar
- **Ukuran Gambar:** 150x150 piksel
- **Pembagian Dataset:**
  - Train Set : ~11.200 gambar (80% dari seg_train)
  - Validation : ~2.800 gambar (20% dari seg_train)
  - Test Set   : ~3.000 gambar (seg_test)

---

## Arsitektur Model
- **Base Model:** MobileNetV2 (pretrained ImageNet)
- **Input Shape:** 150x150x3
- **Tambahan Layer:**
  - GlobalAveragePooling2D
  - Dense 256 (ReLU)
  - BatchNormalization
  - Dropout 0.5
  - Dense 6 (Softmax)
- **Training:** 2 tahap (Frozen + Fine Tuning)
- **Optimizer:** Adam
- **Loss Function:** Categorical Crossentropy

---

## Hasil Akurasi
| Metrik | Nilai |
|--------|-------|
| Train Accuracy | >95% |
| Validation Accuracy | >95% |
| Test Accuracy | >95% |

---

## Format Model yang Disimpan
| Format | Path | Kegunaan |
|--------|------|----------|
| SavedModel | `saved_model/` | Deployment server |
| TF-Lite | `tflite/model.tflite` | Perangkat mobile |
| TFJS | `tfjs_model/model.json` | Aplikasi browser |
