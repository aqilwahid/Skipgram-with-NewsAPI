# Implementasi SkipGram dengan NewsAPI

**Nama:** Ach. Nur Aqil Wahid  
**NIM:** 24/548091/PPA/06917  

## Deskripsi Proyek
Proyek ini bertujuan untuk mengimplementasikan model SkipGram dengan menggunakan data artikel berita tentang teknologi yang diambil dari NewsAPI. Model ini dilatih dengan variasi parameter ukuran jendela (window size) dan dimensi embedding untuk mengevaluasi dampak parameter-parameter tersebut terhadap kualitas word embedding yang dihasilkan.

## Instalasi

1. Clone repository ini:
```bash
git clone https://github.com/username/skipgram-newsapi.git
```

2. Instal dependensi yang dibutuhkan:
```bash
pip install numpy requests scikit-learn
```

3. Dapatkan API Key dari [NewsAPI](https://newsapi.org/) dan masukkan ke dalam kode:
```python
API_KEY = "your-api-key-here"
```

## Cara Menggunakan
Jalankan script utama:

```bash
python skipgram_newsapi.py
```

## Parameter Eksperimen
- **Window Size**: 1, 2, dan 3 (menentukan ukuran konteks di sekitar kata target)
- **Embedding Dimension**: 50, 100, dan 200 (menentukan panjang vektor embedding untuk setiap kata)
- **Epochs**: 10 (jumlah iterasi pelatihan model)

## Hasil Analisis

| Window Size | Embedding Dim | Loss Akhir | Top-5 Similar Words              | Analisis                                      |
|-------------|---------------|------------|---------------------------------|-----------------------------------------------|
| 1           | 50            | 7.2912     | world, of, use, at, next         | Kurang Baik (banyak stopwords muncul)         |
| 1           | 100           | 7.2997     | and, is, to, s, of               | Kurang Baik (stopwords dominan)               |
| 1           | 200           | 7.3120     | digital, ai, innovation, cloud   | Baik (kata relevan ditemukan)                 |
| 2           | 50            | 7.2875     | computing, ai, next, data, world | Baik (kata relevan ditemukan)                 |
| 2           | 100           | 7.2988     | innovation, ai, digital, cloud   | Baik (kata relevan ditemukan)                 |
| 2           | 200           | 7.3050     | digital, computing, ai, data     | Baik (kata relevan ditemukan)                 |
| 3           | 50            | 7.2809     | cloud, ai, digital, data         | Baik (kata relevan ditemukan)                 |
| 3           | 100           | 7.2902     | ai, computing, innovation, cloud | Baik (kata relevan ditemukan)                 |
| 3           | 200           | 7.2971     | digital, innovation, ai, cloud   | Baik (kata relevan ditemukan)                 |

## Kesimpulan
Berdasarkan hasil eksperimen, konfigurasi parameter terbaik adalah **Window Size = 3** dan **Embedding Dimension = 200**. Konfigurasi ini menghasilkan representasi kata yang paling baik secara semantik, terbukti dengan munculnya kata-kata relevan seperti "digital", "innovation", "ai", dan "cloud". Hal ini disebabkan oleh konteks kata yang lebih luas (Window Size besar) dan representasi kata yang lebih detail (Embedding Dimension tinggi).

## Penjelasan tambahan
- Loss yang stabil menunjukkan model telah dilatih dengan baik dan tidak mengalami masalah pelatihan seperti exploding gradient.
- Kata-kata relevan yang muncul menunjukkan model berhasil menangkap hubungan semantik antar kata dari artikel berita bertema teknologi.

---