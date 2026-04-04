# Assignment 2 – Robot Kinematics

## Deskripsi

Program ini merupakan simulasi robot 3 DOF (Degree of Freedom) menggunakan Python, yang terdiri dari:

* Forward Kinematics
* Inverse Kinematics

---

## Struktur File

```
Assignment 2/
├── forward_kinematics.py
├── inverse_kinematics.py
├── main.py
└── __pycache__/   (file otomatis dari Python)
```

---

## Penjelasan `__pycache__`

Folder `__pycache__` berisi file hasil compile otomatis dari Python dengan ekstensi `.pyc`.

Fungsi:

* Mempercepat eksekusi program
* Dibuat otomatis saat program dijalankan

Catatan:

* Bukan bagian utama dari program
* Tidak perlu diedit
* Aman jika dihapus (akan dibuat ulang otomatis)

---

## Forward Kinematics

Digunakan untuk menghitung posisi end-effector berdasarkan sudut joint.

Output:

* Animasi pergerakan robot
* Trajectory end-effector
* Posisi X dan Y

---

## Inverse Kinematics

Digunakan untuk menentukan sudut joint berdasarkan target posisi.

Output:

* Robot mengikuti titik target
* Perbandingan posisi target dan end-effector
* Animasi pergerakan robot

---

## Cara Menjalankan

1. Install library:

```
pip install numpy matplotlib
```

2. Jalankan program:

```
python main.py
```

3. Pilih menu:

* 1 → Forward Kinematics
* 2 → Inverse Kinematics

---

## Parameter Robot

```
L1 = 8
L2 = 6
L3 = 4
```

---

## Catatan

* Sudut menggunakan radian
* Visualisasi menggunakan matplotlib
* Folder `__pycache__` tidak mempengaruhi hasil simulasi

---

## Author

Yosua Dirgana Pratama
