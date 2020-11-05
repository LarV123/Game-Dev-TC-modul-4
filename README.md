# Game-Dev-TC-modul-4
Modul 4 Komunitas Game Dev TC 2020

## Tujuan
1. Peserta dapat menggunakan Tile Map
2. Peserta dapat membuat Animasi

## Tile Map
```Tile map``` adalah komponen yang digunakan untuk menghandle ```Tile Assets``` untuk membuat 2D Levels. Jadi ```Tilemap``` ini akan menyimpan informasi dari objek bertipe ```Tile Assets``` yang nanti akan ditujukan ke komponen ```Tile Renderer``` dan ```Tile Collider```. Dengan ```Tile Map``` kita dapat menyusun level dengan cepat dan mudah.

Jadi secara simple :
- ```Tile Map``` adalah komponen yang menyimpan data-data ```Tile Assets``` yang akan berada di scene.
- ```Tile Renderer``` adalah komponen yang mengambil data dari ```Tile Map``` dan bertugas untuk menggambarkannya ke scene sesuai dengan informasi di ```Tile Asset``` yang disimpan ```Tile Map```.
- ```Tile Collider``` adalah komponen yang digunakan untuk memasang collider2D menurut informasi yang ada di ```Tile Map```. ```Tile Collider``` akan membuat collider sesuai dengan ```Tile Asset``` yang diberikan oleh ```Tile Map```.

### Cara Membuat Tile Asset

1. Buatlah Folder dengan nama "Tile Assets". Folder ini akan digunakan untuk menyimpan Tile Assets kita.
2. Masuk ke dalam folder "Tile Assets". Klik kanan dan pilih create lalu pilih Tile.
3. Beri nama, lalu klik save.
4. Dengan ini akan terbuat asset ```Tile Asset``` yang dengan nama yang kita buat. Jika kita click Tile, maka dalam inspector kita akan melihat data-data dapat kita berikan ke ```Tile Asset``` ini. Disini, kita bisa memasukkan sprite, tipe collider kita, dan warna tint.

Ini adalah salah satu cara membuat Tile Asset. Namun, jika kita melakukan ini untuk setiap sprite maka akan sangat lama dan tidak efektif. Selanjutnya, adalah bagaimana cara kita langsung membuat Tile Asset dengan cepat.

### Cara Cepat Membuat Tile Asset

1. Pertama, buka Tile Pallete window dengan ke Window > 2D > Tile Pallete.
2. Akan terbuka Tile Pallete. Kalian bisa dock window tersebut dengan tekan window tersebut dan arahkan ke suatu tempat.
3. Klik Create New Pallete, Lalu masukkan namanya. Untuk ini akan saya pilih "World 1".
Pallete disini akan mirip seperti color pallete. Dengan ini kita bisa mengelompokkan Tile Asset sesuai dengan penggunaannya. Misalkan ada Tile Pallete untuk Sky, untuk Ground, untuk Building. Dengan ini jika kita ingin membuat level di sky dapat memilih Tile yang pas tanpa terpenuhi oleh Tile yang tidak berhubungan.
4. Klik create lalu pilih folder Tile Assets.
5. Buka folder Sprites. Select semua sprites, lalu drag and drop ke Tile Pallete. Sebelum pilih save, arahkan ke folder Tile Assets. Dengan ini akan terbuat Tile Asset dengan nama sprite dan attribut spritenya sudah sesuai dengan sprite yang di drag tersebut.

### Cara Membuat Tilemap

1. Untuk membuat tile map, klik kanan di hierarchy 2D Objects > Tilemap.
2. Dengan ini akan terbuat 2 Game Objects. Yang pertama bernama Grid dan yang kedua bernama Tilemap. Grid menjadi parent Tile Map. Grid akan berisi komponen grid yang  mendefinisikan bagaimana besar setiap tile. Sedangkan Tilemap akan berisi komponen bernama Tilemap yang akan menyimpan informasi tile yang akan kita render.
3. Untuk menggambar Tile, select game object Tilemap. Maka attribut Active Tilemap akan berubah di Tile Pallete. Pilih satu tile dan pilih tool brush. Arahkan ke scene dan mulai menggambar level yang kalian mau.
4. Untuk memudahkan penggambaran, object square akan dinon-aktifkan terlebih dahulu.
5. Buat level sesuai dengan imajinasi kalian.
Untuk game ini, levelnya akan sebagai berikut.

6. Selanjutnya kita tambahkan komponen ```Tile Collider``` pada object Tile Map. Secara otomatis, akan ada kotak hijau yang menandakan terdapat collider di peta tersebut.
7. Jangan lupa setting layer Tilemap menjadi Ground.

Kita dapat mencoba memainkan gamenya.

Untuk membuat tilemap dengan cell size yang sama, kita dapat langsung membuat empty game object yang menjadi child Grid. Lalu menambahkan komponen ```Tilemap``` dan ```Tilemap Renderer```. Jika membutuhkan collision bisa menambahkan ```Tilemap Collider```.

## Fixing Rigidbody Rotation and Physics Material

Setelah kita memainkan gamenya, ada 2 masalah yang muncul. Pertama player dapat berotasi jika menabrak sesuatu, dan yang kedua pemain akan menempel ke tembok jika kita gerakkan ke arah tembok. 

## Reference
https://docs.unity3d.com/Manual/class-Tilemap.html
