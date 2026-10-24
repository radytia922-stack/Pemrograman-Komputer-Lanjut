# 🧮 Turunan dan Arus Kapasitor (Python SymPy)

Solusi komputasi simbolik untuk latihan Pertemuan 2 mata kuliah **Pemrograman Komputer Lanjut**, Teknik Elektro Universitas Widya Gama Malang.

---

## 📌 Deskripsi Program

Program ini menggunakan library **SymPy** pada Python untuk menghitung turunan pertama dan kedua secara simbolik. Dua kasus yang diselesaikan:

1. Menghitung nilai turunan polinomial biasa.
2. Menghitung arus kapasitor dari fungsi tegangan terhadap waktu.

---

## 🚀 Cara Menjalankan

Pastikan Python 3 sudah terinstal di sistem.

```bash
# 1. Install library SymPy
pip install sympy

# 2. Jalankan script
python latihan_pertemuan2.py
```

---

## 🧠 Cara Kerja Kode

### Soal A — Turunan Polinomial

Fungsi yang dievaluasi:

```
f(t) = 2t³ - 4t² + 6t - 1
```

- Turunan pertama dihitung dengan `sp.diff(f, t)`
- Turunan kedua dihitung dengan `sp.diff(f, t, 2)`
- Nilai pada `t = 2` didapat dengan `.subs(t, 2)`

**Hasil:**

```
f'(t)  = 6t² - 8t + 6
f''(t) = 12t - 8
f'(2)  = 14
```

> Catatan: SymPy mungkin menampilkan `f''(t)` sebagai `4*(3*t - 2)` — nilai yang sama, hanya bentuk faktorisasi berbeda.

---

### Soal B — Arus Kapasitor

Rumus yang digunakan:

```
i_C(t) = C * dv_C(t)/dt
```

Diketahui:
- `C = 220 µF`
- `v(t) = 4t² + 2t` V

**Langkah-langkah:**

1. **Konversi satuan** — `220 µF` diubah ke Farad. Kode pakai `sp.Rational(220, 1000000)` agar tidak kehilangan presisi akibat *floating point*.
2. **Hitung dv/dt** — turunan fungsi tegangan: `sp.diff(v, t)`
3. **Hitung arus** — `i(t) = C * dv/dt`
4. **Evaluasi** — substitusi `t = 3`, lalu kalikan 1000 untuk konversi A → mA

**Hasil:**

```
i(t)      = 0.00022 * (8t + 2)  A
i(t=3)    = 5.72 mA
```

---

## 🔗 Referensi

- Modul Kuliah: Pertemuan 2 Turunan menggunakan Python — Dr. Istiadi, ST., MT.
- [Dokumentasi resmi SymPy](https://docs.sympy.org/)

---

*Tugas Pemrograman Komputer Lanjut — Teknik Elektro, Universitas Widya Gama Malang*
