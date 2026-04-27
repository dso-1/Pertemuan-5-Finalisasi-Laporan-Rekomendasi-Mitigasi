# Pertanyaan Diskusi 5

## 1. Strategi Mitigasi: Fix vs Workaround

Dalam menangani temuan keamanan, tim pengembang dan auditor harus memahami perbedaan antara perbaikan permanen dan solusi sementara.

| Aspek | Fix (Perbaikan Permanen) | Workaround (Solusi Sementara) |
| :--- | :--- | :--- |
| **Definisi** | Mengatasi akar masalah (*root cause*) pada level kode sumber atau arsitektur. | Memberikan lapisan pertahanan tambahan untuk mencegah eksploitasi celah. |
| **Contoh** | Mengganti query SQL mentah dengan *Prepared Statements* (PDO). | Memasang aturan (*rule*) pada WAF untuk memblokir karakter `'` atau `OR 1=1`. |
| **Ketahanan** | Sangat kuat; celah benar-benar tertutup. | Tergantung efektivitas filter; seringkali bisa di-*bypass*. |
| **Utang Teknis** | Rendah; kode menjadi lebih bersih dan standar. | Tinggi; sistem menjadi kompleks karena banyak lapisan tambahan. |

**Kapan Workaround boleh digunakan?**
* **Masa Kritis:** Saat celah bersifat *Zero-Day* dan vendor belum merilis patch resmi.
* **Ketersediaan Layanan:** Jika melakukan perbaikan kode membutuhkan waktu *downtime* yang tidak diizinkan pada jam operasional.
* **Legacy System:** Pada sistem tua yang kodenya terlalu berisiko untuk diubah (rawan merusak fungsi utama).

---

## 2. Etika dan Hukum: Penemuan SQL Injection

Menemukan celah kritis seperti **SQL Injection** yang memungkinkan akses ke database menuntut integritas tinggi dari seorang *security auditor*.

### Sudut Pandang Etika
Seorang praktisi keamanan wajib menghentikan eksploitasi segera setelah mendapatkan bukti keberadaan celah (*Proof of Concept*). Melanjutkan akses untuk melihat atau mengambil data sensitif (seperti data pribadi mahasiswa/dosen) tanpa izin adalah pelanggaran kode etik *White Hat*. Fokus utama laporan adalah memberi tahu pemilik sistem agar segera melakukan perbaikan.

### Sudut Pandang Hukum (UU ITE)
Berdasarkan **UU ITE No. 19 Tahun 2016** (Perubahan UU No. 11 Tahun 2008):
* **Pasal 30:** Mengakses komputer/sistem elektronik milik orang lain secara ilegal adalah tindak pidana.
* **Pasal 32:** Mengubah atau merusak informasi elektronik milik orang lain adalah pelanggaran berat.
**Kesimpulan:** Tanpa izin tertulis (Rules of Engagement), melanjutkan eksploitasi SQL Injection dapat dikategorikan sebagai "Akses Ilegal" meskipun tujuannya adalah pengujian. Laporan wajib diberikan kepada pemilik sistem (Dosen/IT Kampus) sebelum melangkah lebih jauh.

---

## 3. Pentingnya Patch Verification (Verifikasi Penambalan)

Verifikasi penambalan adalah langkah krusial untuk memastikan bahwa mitigasi yang diterapkan benar-benar efektif.

**Mengapa Patch Verification penting?**
1. **Incomplete Fix:** Developer mungkin hanya menutup satu parameter, padahal celah yang sama ada di parameter lain.
2. **Bypass Techniques:** Perbaikan seringkali hanya bersifat "menyaring kata" (seperti memblokir kata `SELECT`), namun tetap bisa ditembus dengan teknik *encoding* atau huruf besar-kecil.
3. **Mencegah False Sense of Security:** Mencegah pemilik sistem merasa sudah aman, padahal pintu serangan masih terbuka sedikit.

**Risiko jika tidak diverifikasi:** Penyerang yang lebih berpengalaman akan menemukan celah sisa tersebut, sementara tim keamanan sudah tidak lagi memantau area tersebut karena dianggap sudah "selesai".

---

## 4. Komunikasi Strategis kepada Pimpinan (Rektor)

Menyampaikan temuan teknis kepada rektor yang tidak memiliki latar belakang IT memerlukan pendekatan bahasa bisnis dan risiko institusi.

**Strategi Penyampaian:**
* **Gunakan Analogi:** Hindari istilah "Time-based Blind SQLi". Gunakan analogi: *"Ada pintu rahasia di sistem jurnal kita yang tidak terkunci, di mana siapa saja dari luar bisa masuk dan mencuri data penelitian atau mengubah nilai akademik secara diam-diam."*
* **Tekankan Dampak Bisnis:** Fokus pada ancaman terhadap akreditasi universitas, tuntutan hukum terkait kebocoran data pribadi (UU PDP), dan kerusakan reputasi institusi di tingkat nasional/internasional.
* **Berikan Solusi, Bukan Hanya Masalah:** Sampaikan langkah-langkah yang diperlukan secara strategis (misal: investasi WAF atau pelatihan *Secure Coding* bagi tim IT internal).

---

## Lampiran: Matriks Risiko (Risk Matrix)

| Business Impact \ Likelihood | VERY LOW | LOW | MEDIUM | HIGH | VERY HIGH |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **VERY HIGH** | | **VU-06** | | **VU-02** | |
| **HIGH** | | **VU-01** | | **VU-03** | |
| **MEDIUM** | | | | **VU-20** | **VU-08** |
| **LOW** | | | | **VU-04** | **VU-05** |
| **VERY LOW** | | | | | |
