<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "8311f46a35cf608c9780f39b62c9dc3f",
  "translation_date": "2025-07-14T02:05:17+00:00",
  "source_file": "05-AdvancedTopics/mcp-root-contexts/README.md",
  "language_code": "id"
}
-->
## Contoh: Implementasi Root Context untuk analisis keuangan

Dalam contoh ini, kita akan membuat root context untuk sesi analisis keuangan, menunjukkan cara mempertahankan status di berbagai interaksi.

## Contoh: Manajemen Root Context

Mengelola root context dengan efektif sangat penting untuk mempertahankan riwayat percakapan dan status. Berikut adalah contoh cara mengimplementasikan manajemen root context.

## Root Context untuk Bantuan Multi-Turn

Dalam contoh ini, kita akan membuat root context untuk sesi bantuan multi-turn, menunjukkan cara mempertahankan status di berbagai interaksi.

## Praktik Terbaik Root Context

Berikut beberapa praktik terbaik untuk mengelola root context secara efektif:

- **Buat Context yang Terfokus**: Buat root context terpisah untuk tujuan atau domain percakapan yang berbeda agar tetap jelas.

- **Tetapkan Kebijakan Kadaluarsa**: Terapkan kebijakan untuk mengarsipkan atau menghapus context lama guna mengelola penyimpanan dan mematuhi kebijakan retensi data.

- **Simpan Metadata yang Relevan**: Gunakan metadata context untuk menyimpan informasi penting tentang percakapan yang mungkin berguna di kemudian hari.

- **Gunakan ID Context Secara Konsisten**: Setelah context dibuat, gunakan ID-nya secara konsisten untuk semua permintaan terkait agar kontinuitas terjaga.

- **Buat Ringkasan**: Ketika context menjadi besar, pertimbangkan untuk membuat ringkasan guna menangkap informasi penting sambil mengelola ukuran context.

- **Terapkan Kontrol Akses**: Untuk sistem multi-pengguna, terapkan kontrol akses yang tepat untuk memastikan privasi dan keamanan context percakapan.

- **Tangani Batasan Context**: Sadari batasan ukuran context dan terapkan strategi untuk menangani percakapan yang sangat panjang.

- **Arsipkan Saat Selesai**: Arsipkan context ketika percakapan selesai untuk membebaskan sumber daya sekaligus menjaga riwayat percakapan.

## Selanjutnya

- [5.5 Routing](../mcp-routing/README.md)

**Penafian**:  
Dokumen ini telah diterjemahkan menggunakan layanan terjemahan AI [Co-op Translator](https://github.com/Azure/co-op-translator). Meskipun kami berupaya untuk mencapai akurasi, harap diperhatikan bahwa terjemahan otomatis mungkin mengandung kesalahan atau ketidakakuratan. Dokumen asli dalam bahasa aslinya harus dianggap sebagai sumber yang sahih. Untuk informasi penting, disarankan menggunakan terjemahan profesional oleh manusia. Kami tidak bertanggung jawab atas kesalahpahaman atau penafsiran yang keliru yang timbul dari penggunaan terjemahan ini.