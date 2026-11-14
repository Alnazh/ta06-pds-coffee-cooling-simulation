# Simulasi Pendinginan Secangkir Kopi

Tugas Akhir 06 - Praktikum Pemodelan dan Simulasi (Sistem Dinamik)

Simulasi suhu secangkir kopi yang mendingin di dalam ruangan (Hukum Pendinginan Newton) dengan model ODE orde 1 dan metode Euler.

## Model

```
dT/dt = -k (T - T_env) + g * u(t)
```

| Simbol | Arti | Nilai |
|--------|------|-------|
| T | Suhu kopi (state variable, controlled variable) | T0 = 90 °C |
| T_env | Suhu ruangan (konstanta / gangguan) | 30 °C |
| k | Konstanta pendinginan | 0,05 /menit |
| g | Gain pemanas | 0,02 °C/menit per % |
| u(t) | Daya pemanas (sinyal kontrol) | 0-100 % |
| Δt | Langkah waktu | 1 menit |

## Skenario simulasi

1. **Steady state** (tanpa pemanas): suhu turun dari 90 °C ke 30 °C.
2. **Sinyal kontrol pemanas**: step, impulse, ramp, dan sinusoida.
3. **Gangguan**: suhu ruangan naik dari 30 °C ke 40 °C pada menit ke-30.

## Struktur

```
main.py              # program utama (menyimpan grafik ke outputs/)
simulasi_kopi.ipynb  # versi notebook (Jupyter / Google Colab)
requirements.txt     # dependensi
outputs/             # grafik hasil simulasi
```

## Cara menjalankan

```bash
pip install -r requirements.txt
python main.py          # simpan grafik ke folder outputs/
python main.py --show   # simpan sekaligus tampilkan jendela grafik
```

Atau buka `simulasi_kopi.ipynb` di Jupyter / Google Colab lalu pilih Run All.

## Hasil singkat

- Tanpa pemanas, suhu akhir 30,13 °C pada menit ke-120 (steady state teori 30 °C), galat Euler maksimum 0,56 °C.
- Step 100 % menuju steady state 70 °C.
- Gangguan ruangan 40 °C menggeser steady state kopi ke 40 °C (konstanta waktu 20 menit).
