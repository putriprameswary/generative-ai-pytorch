# 🤖 Generative AI untuk Vision dan Text menggunakan PyTorch

## 📘 Deskripsi

Repository ini berisi implementasi beberapa model **Generative AI** untuk dua domain utama, yaitu **Vision** (gambar) dan **Text** (teks), menggunakan framework PyTorch.

Pada domain Vision, eksperimen dilakukan menggunakan **Variational Autoencoder (VAE)** dan **Autoencoder (AE)** untuk merekonstruksi sekaligus menghasilkan citra baru dari dataset Fashion-MNIST. Pada domain Text, model **LSTM** dan **GRU** digunakan untuk membangun generator teks karakter-level berbasis cerita pendek berbahasa Indonesia.

Proyek ini dikembangkan sebagai bagian dari tugas mata kuliah *Pembelajaran Mesin Lanjut* untuk memahami bagaimana model generatif mempelajari distribusi data dan menggunakannya untuk menciptakan output baru yang menyerupai data asli.

---

## 🎯 Tujuan

- Memahami konsep dasar Generative AI sebagai pemodelan distribusi data
- Mengimplementasikan VAE dan Autoencoder untuk generasi citra
- Mengimplementasikan LSTM dan GRU untuk generasi teks
- Membandingkan kualitas output, loss, dan efisiensi training
- Menganalisis trade-off antara kompleksitas model dan kemampuan generatif

---

## 📂 Dataset

### 1. Vision: Fashion-MNIST

- 60.000 data training dan 10.000 data testing
- Gambar grayscale berukuran 28×28 piksel
- 10 kategori pakaian

### 2. Text: Cerita Pendek Bahasa Indonesia

- Dataset custom yang disusun sendiri
- 21 kalimat dengan sekitar 1.100 karakter
- Character-level tokenization

---

## 🧠 Model yang Digunakan

### A. Vision Generation

- **Variational Autoencoder (VAE)**
- **Autoencoder (AE)**

Arsitektur umum:

```text
Input → Encoder → Latent Space → Decoder → Output
```

### B. Text Generation

- **LSTM**
- **GRU**

Arsitektur umum:

```text
Input Character → Embedding → RNN Layers → Linear → Prediksi Karakter Berikutnya
```

---

## 📐 Rumus Utama

### Variational Autoencoder (VAE)

```text
z = μ + σ · ε,   ε ~ N(0, I)

L = L_recon + L_KL
L_KL = -0.5 × Σ(1 + log(σ²) - μ² - σ²)
```

### Autoencoder

```text
z  = fθ(x)
x̂ = gφ(z)
L  = ||x - x̂||²
```

### Text Generation

```text
p(x1, x2, ..., xT) = ∏ p(xt | x1, ..., x(t-1))
```
---

## ⚙️ Konfigurasi Training

| Parameter | Vision Models | Text Models |
|--------|--------|--------|
| Optimizer | Adam | Adam |
| Learning Rate | 0.001 | 0.001 |
| Batch Size | 128 | 16 |
| Epoch | 10 | 30 |
| Loss Function | BCE + KL / MSE | CrossEntropy |

---

## 📊 Hasil Eksperimen

### Vision Models

| Model | Kemampuan Generatif | Karakteristik Output |
|------|------|------|
| VAE | Menghasilkan gambar baru | Lebih smooth, sedikit blur |
| Autoencoder | Rekonstruksi saja | Lebih tajam |

### Text Models

| Model | Loss Akhir | Catatan |
|------|------|------|
| LSTM | 0.0514 | Koheren dan stabil |
| GRU | 0.0516 | Lebih sederhana dan cepat |

---

## 🔍 Analisis Singkat

- VAE mampu menghasilkan citra baru karena latent space terstruktur sebagai distribusi probabilistik.
- Autoencoder menghasilkan rekonstruksi lebih tajam, tetapi tidak dapat melakukan sampling untuk generasi data baru.
- LSTM dan GRU menunjukkan performa yang hampir identik pada dataset kecil.
- Nilai loss rendah tidak selalu menjamin kualitas generasi terbaik; evaluasi visual dan koherensi output tetap diperlukan.

---

## 🛠️ Teknologi

- Python
- PyTorch
- Torchvision
- NumPy
- Matplotlib
- Google Colab

---

## 📁 Struktur Repository

```text
.
├── generative_ai.ipynb
├── report.pdf
├── theory_notes.pdf
└── README.md
```

---

## 🚀 Cara Menjalankan

1. Buka notebook `generative_ai.ipynb` di Google Colab.
2. Aktifkan GPU melalui `Runtime → Change runtime type → GPU`.
3. Jalankan seluruh cell secara berurutan.
4. Hasil training, visualisasi, dan output generatif akan muncul pada notebook.

---

## 📌 Kesimpulan

Proyek ini menunjukkan bahwa model generatif dapat diterapkan pada domain gambar maupun teks dengan karakteristik yang berbeda. VAE unggul dalam menghasilkan data baru melalui latent space probabilistik, Autoencoder menghasilkan rekonstruksi yang lebih tajam, sedangkan LSTM dan GRU memberikan performa yang sangat kompetitif untuk generasi teks pada dataset kecil.

---

## 📚 Referensi

1. Kingma, D. P., & Welling, M. (2013). *Auto-Encoding Variational Bayes*.
2. Hochreiter, S., & Schmidhuber, J. (1997). *Long Short-Term Memory*.
3. Cho, K., et al. (2014). *Learning Phrase Representations using RNN Encoder-Decoder*.
4. Xiao, H., et al. (2017). *Fashion-MNIST: A Novel Image Dataset for Benchmarking Machine Learning Algorithms*.
5. PyTorch Documentation: https://pytorch.org/docs

---

## 👤 Author

**Putri Torsia Aura Prameswary**  
NIM: 2546000083  
Mata Kuliah: Topik Kecerdasan Buatan  
Program Studi: Magister Ilmu Komputer  
Universitas Brawijaya

---

## 📌 Catatan

Repository ini dibuat untuk keperluan akademis sebagai implementasi dan analisis model Generative AI pada domain citra dan teks menggunakan PyTorch.
