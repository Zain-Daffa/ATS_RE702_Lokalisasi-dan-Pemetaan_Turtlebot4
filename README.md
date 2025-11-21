# TurtleBot4 - Sistem Navigasi Otonom & Lokalisasi

**Proyek UTS Mata Kuliah Lokalisasi dan Pemetaan (RE702)**  
**Nama:** Muhammad Zainul Daffa  
**NIM:** 4222201049  
**Kelas:** RE 7B Pagi

---

## Ringkasan Proyek

Proyek ini merupakan implementasi sistem navigasi dan lokalisasi untuk robot TurtleBot4 yang dikembangkan sebagai bagian dari evaluasi Ujian Tengah Semester mata kuliah RE702.

**Komponen Sistem:**
- Modul lokalisasi robot dengan AMCL (Adaptive Monte Carlo Localization)
- Stack navigasi Nav2 untuk path planning
- Kontrol pergerakan robot ke koordinat target
- Sistem buzzer terintegrasi sesuai requirement ujian

---

## Konfigurasi Awal

### Membuat Peta Lingkungan

Langkah pertama adalah membuat map dari area pengujian yang akan digunakan.

**Direktori penyimpanan:**
```
maps/
```

**Panduan lengkap:**  
Ikuti tutorial resmi TurtleBot4 untuk pembuatan peta:  
[https://turtlebot.github.io/turtlebot4-user-manual/tutorials/generate_map.html](https://turtlebot.github.io/turtlebot4-user-manual/tutorials/generate_map.html)

### Koneksi dengan Robot

Pastikan komputer development dan TurtleBot4 berada dalam satu network yang sama.

**Akses robot melalui SSH:**
```bash
ssh ubuntu@192.168.185.3
```

---

## Panduan Eksekusi Sistem

### Langkah 1: Menjalankan Localization

Pada **terminal di TurtleBot4**, eksekusi perintah berikut:
```bash
ros2 launch turtlebot4_navigation localization.launch.py map:=path/ke/map.yaml
```

Ganti `path/ke/map.yaml` dengan lokasi file peta Anda.

### Langkah 2: Mengaktifkan Navigation Stack

Buka **terminal baru** di robot, kemudian jalankan:
```bash
ros2 launch turtlebot4_navigation nav2.launch.py
```

### Langkah 3: Membuka RViz untuk Visualisasi

Pada **komputer/laptop development**, jalankan:
```bash
ros2 launch turtlebot4_viz view_navigation.launch.py
```

> **Penting:** Pastikan pose robot di RViz match dengan posisi aktual robot di lapangan. Gunakan tool "2D Pose Estimate" jika diperlukan penyesuaian.

---

## Instalasi Package

### Membuat ROS2 Workspace
```bash
mkdir -p ros2_ws/src
cd ros2_ws/src
```

### Download Repository
```bash
git clone https://github.com/AbdiWijaya02/UTS-RE702---Turtlebot4.git
```

### Kompilasi Package

Kembali ke root workspace dan build:
```bash
cd ../
colcon build
```

### Source Environment
```bash
source install/setup.bash
```

> **Tips:** Tambahkan perintah source ke `~/.bashrc` agar otomatis dijalankan setiap terminal baru:
> ```bash
> echo "source ~/ros2_ws/install/setup.bash" >> ~/.bashrc
> ```

---

## Menjalankan Node Utama

Setelah semua setup selesai, eksekusi node utama dengan perintah:
```bash
ros2 run abdi_pkg abdinode
```

Node ini akan mengendalikan pergerakan robot menuju titik tujuan yang telah ditentukan.

---

## 🎬 Video Demo

- Link YouTube: `https://youtu.be/b6Jc3NDo4qI?si=Upo1l2yUh0Ste9Kz`

---

## 📚 Referensi

- [TurtleBot4 Official Documentation](https://turtlebot.github.io/turtlebot4-user-manual/)
- [ROS2 Navigation Stack (Nav2)](https://navigation.ros.org/)
- [AMCL Localization Package](https://navigation.ros.org/configuration/packages/configuring-amcl.html)

---
