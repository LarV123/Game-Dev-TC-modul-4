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
Setelah kita memainkan gamenya, ada 2 masalah yang muncul. Pertama player dapat berotasi jika menabrak sesuatu, dan yang kedua pemain akan menempel ke tembok jika kita gerakkan ke arah tembok. Mari kita perbaiki bug ini.

### Rigidbody Constraint
Seperti yang kita tahu, ```Rigidbody``` akan mengoverride attribut di transform seperti posisi, rotasi. Dalam ```rigidbody```, kita dapat membuat constraint agar ```rigidbody``` tidak mengubah suatu property dalam transform. Untuk ```Rigidbody2D``` dapat di setting di gambar berikut. Dapat dilihat kita dapat memberikan 3 constraint, yaitu Freeze Position X, Freeze Position Y, dan Freeze Rotation Z.  Sesuai dengan namanya, freeze position X berarti ```Rigidbody``` tidak akan mengubah posisi x object tersebut, kita tetap bisa mengubah valuenya jika mengubah transform akan tetapi ```Rigidbody``` tidak akan mengubah value tersebut sama sekali. Begitu juga berlaku untuk Freeze Position Y. Yang terakhir Freeze Rotation Z berarti Rigidbody tidak akan mengubah rotasi dari transform tersebut akan tetapi kita tetap bisa mengubah rotasi transform menggunakan komponen transform.

### Physics Material
Dalam Collider kita dapat memberikan ```Physics Material```. Secara default, ```Physics Material``` akan diberi friction dan tidak ada bounciness. ```Physics Material``` digunakan untuk mengontrol bagaimana cara ```Rigidbody``` menkalkulasikan kecepatan saat ada collision antara 2 objek.

### Membuat Physics Material
Sebelum membuat Physics Material akan lebih baik membuat folder yang berisi semua Physics Material untuk mengelompokkan dan organizational purposes. Untuk kali ini foldernya akan bernama "Physics Material".

Masuklah ke dalam folder tersebut, lalu klik kanan > Create > Physics Material 2D. Beri nama "Slippery". Setelah itu setting, frictionnya diubah menjadi 0.
Dalam inspector, kita dapat mengubah friction dan bounciness. Friction akan menentukan bagaimana ```Rigidbody``` mengkalkulasikan bagaimana collision antar 2 benda yang bergesekan mengurangi kecepatan. Bounciness akan menentukan bagaimana Rigidbody mengkalkulasikan bagaimana collision antar 2 benda yang berbenturan mengaffect kecepatan. Jika bounciness berisi satu maka, objek yang bertabrakan akan mempunyai kecepatan yang sama namun berlawanan arah.

## Reference
https://docs.unity3d.com/Manual/class-Tilemap.html
