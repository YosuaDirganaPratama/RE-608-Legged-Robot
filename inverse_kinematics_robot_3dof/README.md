# 🤖 Inverse Kinematics Robot Planar 3-DOF

Proyek ini membandingkan beberapa pendekatan untuk menyelesaikan masalah **Inverse Kinematics (IK)** pada robot planar 3-DOF menggunakan:

- Machine Learning (KNN)
- Machine Learning (Random Forest)
- Deep Learning (MLP)
- Reinforcement Learning (PPO)

Tujuan utama proyek adalah memprediksi sudut sendi robot berdasarkan posisi target yang diinginkan sehingga end-effector dapat mencapai target dengan error sekecil mungkin.

---

## 📖 Deskripsi Proyek

Inverse Kinematics (IK) merupakan proses menentukan sudut-sudut sendi robot berdasarkan posisi target yang ingin dicapai.

Pada proyek ini digunakan robot planar 3-DOF dengan tiga buah sendi:

- θ₁ (Shoulder)
- θ₂ (Elbow)
- θ₃ (Wrist)

Input sistem:

- Posisi target (x, y)

Output sistem:

- Sudut sendi (θ₁, θ₂, θ₃)

---

## 🦾 Konfigurasi Robot

### Panjang Link

```python
L1 = 0.5
L2 = 0.4
L3 = 0.3
```

### Jangkauan Maksimum

```python
MAX_REACH = L1 + L2 + L3
```

Hasil:

```text
MAX_REACH = 1.2 meter
```

### Perbandingan Konfigurasi

| Konfigurasi Link | Jangkauan Maksimum |
|-----------------|-------------------|
| [0.4, 0.3, 0.2] | 0.9 m |
| [0.5, 0.4, 0.3] | 1.2 m |

Perubahan panjang link meningkatkan workspace robot sehingga lebih banyak target yang dapat dijangkau.

---

## ⚙️ Alur Program

```text
Forward Kinematics
        ↓
Pembuatan Dataset
        ↓
Train-Test Split
        ↓
Machine Learning
(KNN & Random Forest)
        ↓
Deep Learning (MLP)
        ↓
Reinforcement Learning (PPO)
        ↓
Evaluasi Performa
```

---

## 🔧 Metode yang Digunakan

### 1. K-Nearest Neighbors (KNN)

KNN memprediksi sudut robot berdasarkan data tetangga terdekat dari dataset pelatihan.

#### Kelebihan

- Implementasi sederhana
- Training cepat
- Cocok untuk dataset kecil

#### Kekurangan

- Membutuhkan dataset
- Generalisasi terbatas

---

### 2. Random Forest

Random Forest menggunakan banyak Decision Tree untuk menghasilkan prediksi yang lebih stabil.

#### Parameter Optimasi

```python
RandomForestRegressor(
    n_estimators=300,
    max_depth=20,
    min_samples_split=2,
    min_samples_leaf=1,
    random_state=42
)
```

#### Kelebihan

- Akurasi tinggi
- Tahan terhadap noise
- Mengurangi risiko overfitting

---

### 3. Deep Learning (MLP)

Multi-Layer Perceptron (MLP) mempelajari hubungan non-linear antara posisi target dan sudut sendi robot.

#### Kelebihan

- Akurasi tinggi
- Mampu mempelajari hubungan kompleks

#### Kekurangan

- Membutuhkan dataset besar
- Waktu training lebih lama

---

### 4. Reinforcement Learning (PPO)

Pada metode ini agent belajar sendiri melalui interaksi dengan lingkungan tanpa menggunakan dataset.

#### Fungsi Reward

```text
Reward = -distance(end_effector, target)

Bonus = +10
jika distance < 0.02 m
```

#### Kelebihan

- Tidak membutuhkan dataset
- Cocok untuk lingkungan dinamis

#### Kekurangan

- Waktu training lama
- Membutuhkan banyak eksplorasi

---

## 📊 Pertanyaan Diskusi

### 1. Mengapa Deep Learning lebih akurat daripada KNN meskipun menggunakan dataset yang sama?

Deep Learning mampu mempelajari hubungan non-linear yang kompleks melalui beberapa lapisan neuron sehingga memiliki kemampuan generalisasi yang lebih baik terhadap data baru. Sebaliknya, KNN hanya mengandalkan tetangga terdekat pada dataset sehingga kurang efektif untuk permasalahan yang kompleks seperti inverse kinematics.

### 2. Mengapa Reinforcement Learning tidak membutuhkan dataset tetapi waktu training lebih lama?

Reinforcement Learning belajar melalui proses trial-and-error. Agent harus mencoba banyak aksi, menerima reward, dan memperbaiki kebijakannya secara bertahap. Proses eksplorasi ini membutuhkan banyak episode sehingga waktu training menjadi lebih lama dibandingkan supervised learning.

### 3. Bagaimana cara menambahkan obstacle avoidance pada Reinforcement Learning?

Obstacle avoidance dapat ditambahkan dengan:

- Menambahkan posisi obstacle ke dalam state environment.
- Memberikan reward negatif ketika robot mendekati obstacle.
- Memberikan penalti besar ketika terjadi tabrakan.
- Tetap memberikan reward positif saat berhasil mencapai target.

Dengan cara ini agent akan belajar mencapai target sekaligus menghindari hambatan.

### 4. Apa kelemahan supervised learning untuk inverse kinematics pada konfigurasi robot yang baru?

Model supervised learning sangat bergantung pada data pelatihan. Jika panjang link, batas sudut, atau konfigurasi robot berubah, maka akurasi prediksi dapat menurun dan model perlu dilatih ulang menggunakan dataset yang baru.

---

## 📈 Perbandingan Metode

| Metode | Membutuhkan Dataset | Kecepatan Training | Generalisasi |
|----------|----------|----------|----------|
| KNN | Ya | Cepat | Sedang |
| Random Forest | Ya | Sedang | Baik |
| MLP | Ya | Lambat | Sangat Baik |
| PPO (RL) | Tidak | Sangat Lambat | Sangat Baik |

---

## ✅ Kesimpulan

Pada proyek ini telah dilakukan implementasi dan perbandingan beberapa metode untuk menyelesaikan masalah Inverse Kinematics robot planar 3-DOF.

- KNN memberikan solusi yang sederhana dan cepat.
- Random Forest menghasilkan prediksi yang stabil dan akurat setelah dilakukan optimasi parameter.
- MLP memberikan akurasi tinggi karena mampu mempelajari hubungan non-linear yang kompleks.
- PPO tidak memerlukan dataset dan cocok digunakan pada lingkungan yang dinamis, meskipun membutuhkan waktu training yang lebih lama.

Pemilihan metode terbaik bergantung pada kebutuhan aplikasi, ketersediaan data, dan sumber daya komputasi yang tersedia.

---

## 👨‍💻 Penulis

**Yosua Dirgana Pratama**

Proyek Robotika – Inverse Kinematics Robot Planar 3-DOF