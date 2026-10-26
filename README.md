# Regresi Linier Berganda: Harga Saham S&P 500

Tugas Praktikum Modul 6 (Regresi Linier Berganda dengan Python), mata kuliah **Infrastruktur dan Platform untuk Sains Data**.

**Nama:** Haryo Seno Raihan Maulana Luqman
**Kelas:** DS-05-02

## Studi kasus

Seberapa besar pengaruh laba per saham, dividend yield, dan rasio harga terhadap penjualan terhadap harga saham perusahaan S&P 500, dan seberapa baik kualitas prediksinya?

| Peran | Variabel | Keterangan |
|---|---|---|
| Dependen (Y) | `Price` | Harga saham (USD) |
| Independen (X1) | `Earnings/Share` | Laba per saham (USD) |
| Independen (X2) | `Dividend Yield` | Dividen dibagi harga (%) |
| Independen (X3) | `Price/Sales` | Rasio harga terhadap penjualan |

## Dataset

[S&P 500 Companies with Financial Information](https://www.kaggle.com/datasets/paytonfisher/sp-500-companies-with-financial-information) dari Kaggle (pengunggah: paytonfisher). File `Data/financials.csv` berisi 505 perusahaan dan 14 kolom. Data adalah milik pengunggah aslinya dan disertakan di sini hanya untuk keperluan tugas.

Catatan kualitas data: di file sumber, kolom `52 Week Low` dan `52 Week High` tertukar. Hal ini diperbaiki di notebook.

## Isi repo

| File | Isi |
|---|---|
| `M6_Regression_Analysis.ipynb` | Notebook lengkap beserta output dan interpretasi |
| `Requirements.txt` | Daftar package Python |
| `Data/financials.csv` | Dataset |

## Alur analisis

1. EDA dan pemeriksaan kualitas data
2. Uji asumsi awal: normalitas, linearitas, multikolinearitas (korelasi dan VIF)
3. Train-test split 70:30, lalu `StandardScaler` di-fit hanya pada data latih
4. Model OLS (`statsmodels`)
5. Uji asumsi residual: normalitas, autokorelasi (Durbin-Watson), homoskedastisitas (Breusch-Pagan)
6. Evaluasi: R², MSE, RMSE, MAE
7. Uji-T, uji-F, dan eksperimen pengaruh outlier

## Hasil utama

| Ukuran | Nilai |
|---|---|
| R² latih / uji | 0,347 / 0,490 |
| MAE / RMSE (data uji) | ≈ 45 USD / ≈ 114 USD |
| Uji-F | F ≈ 61,75; p ≈ 4,76 × 10⁻³² (model layak) |
| Fitur paling berpengaruh | `Earnings/Share` (koefisien standar 0,519) |

Ketiga fitur signifikan secara statistik. Asumsi multikolinearitas dan autokorelasi terpenuhi, linearitas terpenuhi sebagian, sedangkan normalitas residual dan homoskedastisitas tidak terpenuhi.

## Cara menjalankan

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux/macOS
source .venv/bin/activate

pip install -r Requirements.txt
```

Buka `M6_Regression_Analysis.ipynb` di Jupyter, pilih kernel dari `.venv`, lalu jalankan **Restart Kernel and Run All Cells**.
