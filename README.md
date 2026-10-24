# 🧮 Integral dan Aplikasi Teknik Elektro (Python SymPy)

Materi dan solusi komputasi simbolik untuk Pertemuan 3 mata kuliah **Pemrograman Komputer Lanjut**, Teknik Elektro Universitas Widya Gama Malang.

---

## 📌 Deskripsi Program

Program ini menggunakan library **SymPy** pada Python untuk menyelesaikan operasi integral simbolik. Ada tiga penerapan komputasi utama yang dibahas:

1. Integral dasar (tentu dan tak tentu).
2. Menghitung energi listrik dari fungsi daya.
3. Menghitung tegangan kapasitor dari fungsi arus dengan memasukkan kondisi awal.

---

## 🚀 Cara Menjalankan

Pastikan Python 3 sudah terinstal.

```bash
# 1. Install library SymPy
pip install sympy

# 2. Jalankan script
python latihan_pertemuan3.py
```

---

## 🧠 Rangkuman Materi

Turunan menyatakan laju perubahan, sedangkan integral membantu kita mendapatkan kembali fungsi akumulasi atau antiturunannya.

### 1. Integral Tak Tentu dan Kondisi Awal

Fungsi `sp.integrate(f, t)` digunakan untuk mencari antiturunan dasar. SymPy tidak otomatis menambahkan konstanta integrasi (`K`) pada outputnya. Nilai `K` harus dihitung dan ditambahkan secara manual dengan mensubstitusi nilai dari kondisi awal yang diketahui.

### 2. Integral Tentu

Integral tentu menghitung akumulasi nilai pada interval waktu spesifik. Syntax yang digunakan:

```python
sp.integrate(f, (t, awal, akhir))
```

Fungsi yang bernilai negatif akan mengurangi total akumulasi, sehingga hasil bisa nol jika area positif dan negatif saling meniadakan.

### 3. Aplikasi di Teknik Elektro

**Energi Listrik:**
Energi (Joule) didapat dengan mengintegralkan fungsi daya terhadap waktu. Konversi ke Watt-hour (Wh): bagi dengan 3600. Daya rata-rata = total energi dibagi durasi waktu.

**Tegangan Kapasitor:**
Persamaan fisiknya:

```
vC(t) = vC(0) + (1/C) * integral( iC(t) dt )
```

Selalu gunakan `sp.Rational` untuk nilai kapasitansi (misalnya mikroFarad) agar perhitungan simbolik tetap eksak dan tidak terpengaruh *floating point*.

---

## 📝 Pembahasan Latihan Soal

### Soal A — Integral Polinomial

**Soal:** Diketahui `f(t) = 8t + 3`. Tentukan antiturunan dan hasil integral pada rentang 0–2.

**Cara Kerja:**
1. Hitung antiturunan dengan `sp.integrate(f, t)`, lalu tambahkan konstanta `K`.
2. Hitung integral tentu dengan `sp.integrate(f, (t, 0, 2))`.

**Hasil:**

```
F(t)        = 4t² + 3t + K
Integral[0,2] = 22
```

---

### Soal B — Energi dan Daya Rata-rata

**Soal:** Diketahui `P(t) = 15 + 3t` W pada interval 0–4 sekon. Cari energi (J dan Wh) serta daya rata-rata.

**Cara Kerja:**
1. Integralkan `P(t)` dari `t=0` sampai `t=4` → dapat nilai Joule.
2. Bagi dengan 3600 → dapat nilai Wh.
3. Bagi total energi (J) dengan durasi 4 s → dapat daya rata-rata.

**Hasil:**

```
Energi        = 84 J  =  0.023333 Wh
Daya rata-rata = 21 W
```

---

### Soal C — Tegangan Kapasitor

**Soal:** Diketahui `C = 200 µF`, arus konstan `i = 2 mA`, tegangan awal `vC(0) = 1 V`. Cari persamaan `vC(t)` dan nilainya saat `t = 0.3 s`.

**Cara Kerja:**
1. Konversi ke satuan standar menggunakan `sp.Rational`:
   - `C = 200/1_000_000` F
   - `i = 2/1000` A
2. Integralkan arus terhadap waktu, bagi dengan `C`, tambahkan kondisi awal `1 V`.
3. Substitusi `t = 3/10` untuk mendapat tegangan spesifik.

**Hasil:**

```
vC(t)    = 10t + 1  V
vC(0.3s) = 4 V
```

---

## 🔗 Referensi

- Modul Kuliah: Pertemuan 3 Integral menggunakan Python — Dr. Istiadi, ST., MT.
- [Dokumentasi resmi SymPy](https://docs.sympy.org/)

---

*Tugas Pemrograman Komputer Lanjut — Teknik Elektro, Universitas Widya Gama Malang*
