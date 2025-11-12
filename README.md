# TA3PJK

Link Youtube : https://youtu.be/xP_uCoWejwY?si=K7n5d0g8cWsaMScw 
Packet Tracer : https://github.com/AlyaNayraSyafiqa/TA3PJK/blob/main/TUGAS%20AKHIR%203_ALYA%20NAYRA%20SYAFIQA_2315061001.pkt 

### 1. **Membangun Topologi**
- Hubungkan dua switch (S1 dan S2) menggunakan kabel straight-through pada port FastEthernet0/1.
- Hubungkan PC-A ke switch S1.
- Hubungkan PC-B dan PC-C ke switch S2.
- Gunakan kabel Copper Straight-Through untuk semua koneksi.
- Nyalakan semua perangkat agar port aktif.

### 2. **Konfigurasi Dasar Switch**
- Ganti nama (hostname) setiap switch.
- Tambahkan password untuk mode console, vty, dan privileged EXEC
- Aktifkan enkripsi password dan tambahkan banner peringatan.
- Konfigurasikan alamat IP pada VLAN 99 untuk keperluan manajemen switch
- Matikan (shutdown) semua port yang tidak digunakan untuk meningkatkan keamanan jaringan.

### 3. **Membuat dan Menamai VLAN**
Setiap switch dibuat beberapa VLAN berikut:
- VLAN 10 Operations
- VLAN 20 Parking_Lot 
- VLAN 99 Management  
- VLAN 1000 Native VLAN

### 4. **Mengatur Port VLAN**
- PC-A dimasukkan ke VLAN 10 (Operations).  
- PC-B dimasukkan ke VLAN 10 (Operations).  
- PC-C dimasukkan ke VLAN 20 (Parking_Lot).  
- VLAN 99 digunakan untuk alamat IP manajemen di setiap switch.

### 5. **Membuat Trunk Antar Switch**
- Port FastEthernet0/1 pada kedua switch diatur sebagai **trunk port**.  
- Trunk berfungsi untuk membawa lalu lintas dari VLAN 10, 20, 99, dan 1000 melalui satu koneksi antar switch.  
- Native VLAN diubah dari default VLAN 1 ke VLAN 1000 agar lebih aman dan tidak bercampur dengan lalu lintas data pengguna.

### 6. **Pengujian Konektivitas**
<img width="597" height="706" alt="image" src="https://github.com/user-attachments/assets/ed4c339d-aa5e-4c5a-89b5-553bed869e41" />
<img width="703" height="122" alt="image" src="https://github.com/user-attachments/assets/c63d7776-3d6e-4b86-a4c2-c21c36bf1f26" />

| Pengujian | Hasil | Penjelasan |
|------------|--------|-------------|
| PC-A ke PC-B | Berhasil | Keduanya berada di VLAN 10 (Operations) |
| PC-A ke PC-C | Gagal | Berbeda VLAN (10 dan 20), tidak dapat berkomunikasi tanpa inter-VLAN routing |
| S1 ke S2 | Berhasil | Keduanya menggunakan VLAN 99 (Management) melalui trunk |
| PC-A ke S1 | Gagal | Tidak ada perangkat Layer 3 untuk menghubungkan VLAN 10 dan 99 |

## Analisis
- **VLAN** memisahkan domain broadcast untuk meningkatkan efisiensi dan keamanan.  
- **Trunk** memungkinkan beberapa VLAN mengalir melalui satu jalur fisik antar switch.  
- **Inter-VLAN Routing** dibutuhkan agar perangkat dari VLAN berbeda bisa saling berkomunikasi.  
- Mengubah **Native VLAN** ke VLAN lain (selain VLAN 1) mencegah potensi penyadapan atau konflik konfigurasi.

## Manfaat Implementasi VLAN
1. **Keamanan** meningkat karena setiap grup pengguna terisolasi.  
2. **Efisiensi bandwidth** dengan mengurangi broadcast domain.  
3. **Kemudahan manajemen**, karena pengelompokan berdasarkan fungsi atau departemen.  
4. **Fleksibilitas tinggi**, memungkinkan perubahan topologi tanpa memengaruhi struktur fisik jaringan.

## Kesimpulan
Konfigurasi VLAN dan trunking ini menunjukkan bagaimana dua switch dapat saling berkomunikasi sambil mempertahankan segmentasi jaringan.  
PC pada VLAN yang sama dapat berkomunikasi tanpa masalah, sedangkan antar VLAN membutuhkan perangkat Layer 3.  
Implementasi VLAN terbukti membantu meningkatkan efisiensi, keamanan, dan keteraturan jaringan di lingkungan perusahaan.
