## Database Smells

+ **Multipurpose column**<br/>
  Jika sebuah kolom digunakan untuk beberapa tujuan, dimungkinkan terdapat code tambahan agar data tersebut tetap valid. sebagai contoh:
  - sebuah kolom yang menyimpan data tanggal lahir jika seseorang tsb merupakan pelanggan atau tanggal mulai bekerja jika seseorang tsb merupakan pegawai
+ **Multipurpose table**<br/>
  Jika sebuah tabel digunakan untuk menyimpan data untuk beberapa jenis entity, dimungkinkan indikasi dari design yang cacat. sebagai contoh:
  - sebuah tabel pelanggan yg bersifat generik digunakan untuk menyimpan data kustomer, jenis orang dan organisasi. permasalahan dg pendekatan seperti ini adalah struktur data untuk orang dan organisasi berbeda, seperti entity orang memiliki nama depan, nama tengah, dan nama akhir sementara organisasi hanya nama, sehingga akan terdapat kolom yang bernilai NULL karena perbedaan jenis kustomer ini.
+ **Redundant data**<br/>
  Redundant berarti terdapat data yang sama tersimpan dibeberapa tempat, besar kemungkinan terdapat inkonsistensi data. sebagai contoh:
  - data alamat pelanggan disimpan dalam beberapa tabel
+ **Tables with too many columns**<br/>
  Tabel dengan banyak kolom merupakan indikasi rancangan yg mencoba menyimpan data beberapa entitas dalam satu tabel. contoh:
  - Tabel customer mengandung kolom untuk menyimpan berbagai jenis alamat (pengiriman, tagihan, tempat tinggal)
  - Tabel customer mengandung kolom untuk menyimpan berbagai jenis telepon (rumah, kerja, seluler)
+ **Tables with too many rows**<br/>
  Tabel yang besar merupakan indikasi permasalah performa. Sebagai contoh, akan sangat time-consuming untuk mencari tabel dengan jutaan baris. Sebaiknya data tersebut dipisah secara vertikal dengan memindahkan sebagian kolom kedalam tabel yang lain, atau pisah secara horizontal dengan memindahkan sebagian kedalam tabel yang lain (database sharding).
+ **"Smart" columns**<br/>
  Jika suatu kolom akan membuat perubahan pada data yang lain. contoh:
  - Empat digit pertama pada Client ID mengindikasikan cabang kantor dan untuk mendapatkan data cabang kantor ini, harus parsing data dari Client ID ini
  - Suatu kolom yang menyimpan data struktur XML, sehingga untuk mendapatkan data, harus melakukan parsing
+ **Fear of change**<br/>
  Fear of change merupakan indikasi bahwa design schema yang dirty dan perlu di refactor