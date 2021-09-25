# Jarkom-Modul-1-E09-2021

## Anggota
### 1. Dwinanda Bagoes Ansori (05111940000010)
### 2. Bayu Eka Prawira (05111940000042)
### 3. Kelvin Andersen (05111940000080)

<br><br><br>

## 1. Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!
Dengan menggunakan Wireshark filter expression: ```http.host == ichimarumaru.tech``` didapatkan dua paket sebagai berikut \
![1_1](./Picture/No1_1.png) \
Pada paket paling atas, kita follow TCP Stream dan menampilkan informasi sebagai berikut \
![1_2](./Picture/No1_2.png) \
Sehingga didapatkan webserver yang digunakan pada "ichimarumaru.tech" adalah **nginx/1.18.0 (Ubuntu)**

## 2. Temukan paket dari web-web yang menggunakan basic authentication method!
Dengan menggunakan Wireshark filter expression: ```http.authbasic``` didapatkan tiga paket sebagai berikut \
![2_1](./Picture/No2_1.png) \
Dapat dilihat pada detail, terdapat informasi **Authorization : Basic**

## 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
Dari hasil temuan paket dari nomor 2, pada informasi *Authorization : Basic* terdapat *Credentials : kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN* yang merupakan username : ```kuncimenujulautan``` dan password : ```tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN``` \
![3_1](./Picture/No3_1.png) \
Lalu menjawab yang ada dalam basic.ichimarumaru.tech yang merupakan soal untuk menyebutkan urutan konfigurasi pengkabelan T568A
```
Urutan ke 1 : Putih Hijau TD+ (data kirim+)
Urutan ke 2 : Hijau TD- (data kirim-)
Urutan ke 3 : Putih Orange RD+ (data terima +)
Urutan ke 4 : Biru NC (tidak dipakai)
Urutan ke 5 : Putih Biru NC (tidak dipakai)
Urutan ke 6 : Orange RD- (data terima -)
Urutan ke 7 : Putih Coklat NC (tidak dipakai)
Urutan ke 8 : Coklat NC (tidak dipakai)
``` 
![3_2](./Picture/No3_2.png)

## 4. Temukan paket mysql yang mengandung perintah query select!
Dengan menggunakan Wireshark filter expression: ```mysql contains "select" or mysql contains "SELECT"``` didapatkan tiga paket sebagai berikut \
![4_1](./Picture/No4_1.png) \

## 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
Dengan menggunakan Wireshark filter expression: ```mysql contains INSERT``` didapatkan satu paket sebagai berikut \
![5_1](./Picture/No5_1.png) \
Dan didapatkan informasi username : "akakanomi" dan password : "pemisah4lautan". \
Lalu mengerjakan soal pada portal.ichimarumaru.tech untuk menyebutkan urutan konfigurasi pengkabelan T568B
```
Urutan ke 1 : Putih Orange RD+ (data terima+)
Urutan ke 2 : Orange RD- (data terima-)
Urutan ke 3 : Putih Hijau TD+ (data kirim +)
Urutan ke 4 : Biru NC (tidak dipakai)
Urutan ke 5 : Putih Biru NC (tidak dipakai)
Urutan ke 6 : Hijau TD- (data kirim -)
Urutan ke 7 : Putih Coklat NC (tidak dipakai)
Urutan ke 8 : Coklat NC (tidak dipakai)
```
![5_2](./Picture/No5_2.png)

## 6. Cari username dan password ketika melakukan login ke FTP Server!
Dengan menggunakan Wireshark filter expression: ```ftp``` didapatkan paket-paket sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134762467-c5529531-3f24-4635-87fe-c64c22ef8dca.png) \
Dan didapatkan informasi username : "secretuser" dan password : "aku.pengen.pw.aja".

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")
Dengan menggunakan ASCII to Hex converter dan memasukkan "Real.pdf", nilai Hex "52 65 61 6c 2e 70 64 66" didapatkan. Setelah itu pada Wireshark diklik tombol Edit -> Find Packet -> Hex Value dan dimasukkan nilai "52 65 61 6c 2e 70 64 66", sehingga menampilkan beberapak paket sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134762581-298d555a-75f1-4719-93f4-7611b364e3b2.png) \
Pada paket tersebut, kita follow TCP stream dan klik "Show data as Raw", lalu kita menyimpan sebagai Real.pdf dan membuka file tersebut sehingga terdapat gambar sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134762678-8413389c-5cea-4fef-8825-af237c527c8b.png)

## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!
Dengan menggunakan Wireshark filter expression: ```ftp-data.command contains RETR``` tidak ditemukan paket pada Wireshark. \
![image](https://user-images.githubusercontent.com/7587945/134762779-15129994-61ec-4b7d-85ab-1c0fe3e9f216.png)

## 9. Dari paket-paket yang menuju FTP terdapat indikasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
Dengan menggunakan Wireshark filter expression: ```ftp-data.command contains "secret.zip"``` ditemukan paket-paket sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134762837-9dcdd1ed-b4cf-4ddf-b126-c62d0f0a3587.png) \
Pada paket tersebut, kita follow TCP Stream, lalu klik "Show data as Raw", lalu kita menyimpan sebagai secret.zip sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134762919-3910c5f3-8dcd-471e-ac5e-7d57a23750ca.png) \
Setelah itu akan diminta password yang didapatkan pada nomor 10. \
![image](https://user-images.githubusercontent.com/7587945/134762947-c965cb9c-cfb4-4860-a0f9-f12460e72a75.png)

## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
Dengan menggunakan Wireshark filter expression: ```ftp-data.command contains “history.txt”``` ditemukan satu paket sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134762998-aeb8baca-e575-49b1-9cc1-83743e5b4bec.png) \
Didapatkan informasi bahwa alur menuju password secret.zip disimpan dalam variabel $key, yang merupakan isi dari file bukanapaapa.txt \
Dengan menggunakan Wireshark filter expression: ```ftp-data.command contains “bukanapaapa.txt”``` ditemukan satu paket sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134763083-ad3953e9-f56e-45da-87df-efe1e8bed02f.png) \
Didapatkan isi “d1b1langbukanapaapajugagapercaya” yang merupakan password dari file secret.zip, sehingga pada file secret.zip didapatkan file Wanted.pdf dengan isi sebagai berikut \
![image](https://user-images.githubusercontent.com/7587945/134763164-1405495c-14ab-4fd4-80bd-66b303d1b7fe.png)

## 11. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!
Dengan menggunakan capture filter pada Wireshark dengan expression : ```src port 80``` sehingga didapatkan paket sebagai berikut \
![11 ss port 80](https://user-images.githubusercontent.com/81345045/134766135-343d03b5-486f-4b24-afa6-d0e3c35404e0.jpg) \

## 12. Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!
Connect ke server FTP kemudian, ambil paket dengan menggunakan capture filter pada Wireshark dengan expression ```port 21``` dan source ``` Adapter for loopback traffic capture``` sehingga didapatkan paket sebagai berikut \
![12 ss port 21](https://user-images.githubusercontent.com/81345045/134766138-d661db13-7cfa-44b8-bcf0-2ec10aa25b9f.jpg) \
Kendala : paket tidak ada yang terbaca
Solusi : menggunakan FTP dan source ``` Adapter for loopback traffic capture```

## 13. Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!
Dengan menggunakan capture filter pada Wireshark dengan expression : ```dst port 443``` sehingga didapatkan paket sebagai berikut \
![13 ss port 443](https://user-images.githubusercontent.com/81345045/134766142-a1ffa2ff-91bd-4515-8040-560cf1fee13a.jpg) \

## 14. Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!
Dengan menggunakan capture filter pada Wireshark dengan expression : ```dst host kemenag.go.id``` sehingga didapatkan paket sebagai berikut \
![14 ss kemenag](https://user-images.githubusercontent.com/81345045/134766144-4a9a9576-ced8-4e50-b5b3-9d1370157af3.jpg) \

## 15. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Dapatkan IP melalui command prompt dengan expression: ```ipconfig```\
![15 ss ipconfig](https://user-images.githubusercontent.com/81345045/134766148-ab21b480-e73a-4b3a-9ff2-dbafcce671b6.JPG) \
Dengan menggunakan capture filter pada Wireshark dengan expression : ```src host [IP yang telah didapat]``` sehingga didapatkan paket sebagai berikut \
![15 ss capture ip](https://user-images.githubusercontent.com/81345045/134766155-1d66ab3d-638e-41fe-a146-c7109befbda6.JPG) \	
