# Klasifikasi Pemandangan & Rekomendasi Destinasi Wisata Indonesia
## Sistem Rekomendasi Waktu Terbaik Berkunjung Berbasis CNN

---

## Deskripsi Proyek
Proyek ini membangun model **Sequential Convolutional Neural Network (CNN)** untuk mengklasifikasikan jenis pemandangan dari 
sebuah foto ke dalam 4 kategori, sekaligus memberikan rekomendasi destinasi wisata Indonesia beserta waktu terbaik berkunjung berdasarkan musim.

---

## Arsitektur Model
- **Tipe Model:** Sequential CNN (Convolutional Neural Network)
- **Input Shape:** 150x150x3

### Susunan Layer:
| Layer | Konfigurasi | Output Shape |
|-------|------------|--------------|
| Conv2D | 32 filter, kernel 3x3, ReLU, padding same | 150x150x32 |
| BatchNormalization | - | 150x150x32 |
| MaxPooling2D | pool size 2x2 | 75x75x32 |
| Conv2D | 64 filter, kernel 3x3, ReLU, padding same | 75x75x64 |
| BatchNormalization | - | 75x75x64 |
| MaxPooling2D | pool size 2x2 | 37x37x64 |
| Conv2D | 128 filter, kernel 3x3, ReLU, padding same | 37x37x128 |
| BatchNormalization | - | 37x37x128 |
| MaxPooling2D | pool size 2x2 | 18x18x128 |
| Flatten | - | 41472 |
| Dense | 256 neuron, ReLU | 256 |
| Dropout | rate 0.5 | 256 |
| Dense (Output) | 6 neuron, Softmax | 6 |

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

## Hasil Akurasi
| Metrik | Nilai |
|--------|-------|
| Train Accuracy | 92% |
| Validation Accuracy | 92% |
| Test Accuracy | 92% |

---

## Format Model yang Disimpan
| Format | Path | Kegunaan |
|--------|------|----------|
| SavedModel | `saved_model/` | Deployment server |
| TF-Lite | `tflite/model.tflite` | Perangkat mobile |
| TFJS | `tfjs_model/model.json` | Aplikasi browser |
