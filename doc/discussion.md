# Jawaban Pertanyaan Diskusi — Pertemuan 5

**1. Perbedaan antara Fix dan Workaround? Kapan workaround boleh digunakan?**
* **Fix:** Perbaikan permanen pada akar masalah (misal: memperbaiki kode sumber).
* **Workaround:** Solusi sementara untuk mengurangi risiko tanpa memperbaiki kode (misal: memblokir akses lewat firewall).
* **Penggunaan:** Workaround digunakan saat *patch* resmi belum tersedia atau saat perbaikan permanen membutuhkan waktu lama untuk diuji sementara sistem harus tetap aman.

**2. Etika pelaporan SQL Injection sebelum eksploitasi lanjut?**
Sangat wajib. Dari sudut pandang etika (Responsible Disclosure) dan hukum (UU ITE), mengeksploitasi lebih jauh tanpa izin dapat dianggap sebagai tindakan ilegal. Setelah menemukan bukti awal (PoC), segera lapor ke dosen/pemilik sistem agar mitigasi bisa dilakukan tanpa merusak integritas data.

**3. Mengapa patch verification penting? Apa risikonya jika tidak diverifikasi?**
Verifikasi memastikan bahwa mitigasi benar-benar menutup celah tanpa merusak fungsi aplikasi lainnya. Risikonya adalah "False Sense of Security", di mana tim merasa sudah aman padahal celah masih bisa ditembus dengan variasi serangan yang sedikit berbeda.

**4. Cara menyampaikan temuan kepada Rektor (Non-Teknis)?**
Fokus pada **dampak bisnis dan reputasi**. Hindari istilah teknis seperti "Time-based Blind SQLi". Gunakan bahasa: "Ditemukan pintu terbuka yang memungkinkan orang luar mencuri naskah penelitian berharga universitas. Hal ini dapat menurunkan nilai akreditasi jurnal jika tidak segera diperbaiki dalam minggu ini."
