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

![img](img/Creating-Tile.png)

2. Masuk ke dalam folder "Tile Assets". Klik kanan dan pilih create lalu pilih Tile.

![img](img/Creating-Tile.png)

3. Beri nama, lalu klik save.

![img](img/Saving-Tile-Asset.png)

4. Dengan ini akan terbuat asset ```Tile Asset``` yang dengan nama yang kita buat. Jika kita click Tile, maka dalam inspector kita akan melihat data-data dapat kita berikan ke ```Tile Asset``` ini. Disini, kita bisa memasukkan sprite, tipe collider kita, dan warna tint.

![img](img/Tile-Asset-Created.png)

![img](img/Tile-Asset-Inspector.png)

Ini adalah salah satu cara membuat Tile Asset. Namun, jika kita melakukan ini untuk setiap sprite maka akan sangat lama dan tidak efektif. Selanjutnya, adalah bagaimana cara kita langsung membuat Tile Asset dengan cepat.

### Cara Cepat Membuat Tile Asset

1. Pertama, buka Tile Pallete window dengan ke Window > 2D > Tile Pallete.

![img](img/Open-Tile-Pallete.png)

2. Akan terbuka Tile Pallete. Kalian bisa dock window tersebut dengan tekan window tersebut dan arahkan ke suatu tempat.
3. Klik Create New Pallete, Lalu masukkan namanya. Untuk ini akan saya pilih "World 1". Klik create lalu pilih folder Tile Assets.

![img](img/Create-New-Pallete.png)

![img](img/Create-New-Pallete-Window.png)

Pallete disini akan mirip seperti color pallete. Dengan ini kita bisa mengelompokkan Tile Asset sesuai dengan penggunaannya. Misalkan ada Tile Pallete untuk Sky, untuk Ground, untuk Building. Dengan ini jika kita ingin membuat level di sky dapat memilih Tile yang pas tanpa terpenuhi oleh Tile yang tidak berhubungan.

5. Buka folder Sprites. Select semua sprites, lalu drag and drop ke Tile Pallete. Sebelum pilih save, arahkan ke folder Tile Assets. Dengan ini akan terbuat Tile Asset dengan nama sprite dan attribut spritenya sudah sesuai dengan sprite yang di drag tersebut.

6. Akan diminta tempat penyimpanan. Navigasikan ke folder Tile Assets. Lalu pilih save.

![img](img/Saving-Tile-Asset.png)

### Cara Membuat Tilemap

1. Untuk membuat tile map, klik kanan di hierarchy 2D Objects > Tilemap.

![img](img/Create-Tilemap.png)

2. Dengan ini akan terbuat 2 Game Objects. Yang pertama bernama Grid dan yang kedua bernama Tilemap. Grid menjadi parent Tile Map. Grid akan berisi komponen grid yang  mendefinisikan bagaimana besar setiap tile. Sedangkan Tilemap akan berisi komponen bernama Tilemap yang akan menyimpan informasi tile yang akan kita render.

3. Untuk menggambar Tile, select game object Tilemap. Maka attribut Active Tilemap akan berubah di Tile Pallete. Pilih satu tile dan pilih tool brush. Arahkan ke scene dan mulai menggambar level yang kalian mau.

![img](img/Brush-Tilemap.png)

4. Untuk memudahkan penggambaran, object square akan dinon-aktifkan terlebih dahulu.
5. Buat level sesuai dengan imajinasi kalian.
Untuk game ini, levelnya akan sebagai berikut.

![img](img/Level-1.png)

6. Selanjutnya kita tambahkan komponen ```Tile Collider``` pada object Tile Map. Secara otomatis, akan ada kotak hijau yang menandakan terdapat collider di peta tersebut.
7. Jangan lupa setting layer Tilemap menjadi Ground.

Kita dapat mencoba memainkan gamenya.

Untuk membuat tilemap dengan cell size yang sama, kita dapat langsung membuat empty game object yang menjadi child Grid. Lalu menambahkan komponen ```Tilemap``` dan ```Tilemap Renderer```. Jika membutuhkan collision bisa menambahkan ```Tilemap Collider```.

## Fixing Rigidbody Rotation and Physics Material
Setelah kita memainkan gamenya, ada 2 masalah yang muncul. Pertama player dapat berotasi jika menabrak sesuatu, dan yang kedua pemain akan menempel ke tembok jika kita gerakkan ke arah tembok. Mari kita perbaiki bug ini.

![img](img/Bug-1.png)

![img](img/Bug-2.png)

### Rigidbody Constraint
Seperti yang kita tahu, ```Rigidbody``` akan mengoverride attribut di transform seperti posisi, rotasi. Dalam ```rigidbody```, kita dapat membuat constraint agar ```rigidbody``` tidak mengubah suatu property dalam transform. Untuk ```Rigidbody2D``` dapat di setting di gambar berikut. Dapat dilihat kita dapat memberikan 3 constraint, yaitu Freeze Position X, Freeze Position Y, dan Freeze Rotation Z.  Sesuai dengan namanya, freeze position X berarti ```Rigidbody``` tidak akan mengubah posisi x object tersebut, kita tetap bisa mengubah valuenya jika mengubah transform akan tetapi ```Rigidbody``` tidak akan mengubah value tersebut sama sekali. Begitu juga berlaku untuk Freeze Position Y. Yang terakhir Freeze Rotation Z berarti Rigidbody tidak akan mengubah rotasi dari transform tersebut akan tetapi kita tetap bisa mengubah rotasi transform menggunakan komponen transform.

![img](img/Rigidbody-Constraint.png)

### Physics Material
Dalam Collider kita dapat memberikan ```Physics Material```. Secara default, ```Physics Material``` akan diberi friction dan tidak ada bounciness. ```Physics Material``` digunakan untuk mengontrol bagaimana cara ```Rigidbody``` menkalkulasikan kecepatan saat ada collision antara 2 objek.

### Membuat Physics Material
Sebelum membuat Physics Material akan lebih baik membuat folder yang berisi semua Physics Material untuk mengelompokkan dan organizational purposes. Untuk kali ini foldernya akan bernama "Physics Material".

Masuklah ke dalam folder tersebut, lalu klik kanan > Create > Physics Material 2D. Beri nama "Slippery". Setelah itu setting, frictionnya diubah menjadi 0.
Dalam inspector, kita dapat mengubah friction dan bounciness. Friction akan menentukan bagaimana ```Rigidbody``` mengkalkulasikan bagaimana collision antar 2 benda yang bergesekan mengurangi kecepatan. Bounciness akan menentukan bagaimana Rigidbody mengkalkulasikan bagaimana collision antar 2 benda yang berbenturan mengaffect kecepatan. Jika bounciness berisi satu maka, objek yang bertabrakan akan mempunyai kecepatan yang sama namun berlawanan arah.

![img](img/Physics-Material-Create.png)

![img](img/Physics-Material-Inspector.png)

Setelah membuat physics material. Klik object tilemap, lalu masukkan physics material ke dalam kolom physics material di Collider.

![img](img/Collider-Physics-Material-Attribute.png)

## Animation
Animasi merupakan hal yang penting dalam game. Animasi dalam game unity dihandle menggunakan Finite State Machine. Dimana kita akan mendefinisikan beberapa state, lalu kita dapat memberikan transisi antar state sesuai dengan variable yang kita buat di Animator tersebut. Script akan mengakses value variable di animator ini. Setiap state akan berisi informasi keyframe.

Sebelum belajar animation, kita buka window Animation dan window Animator.

![img](img/Animations-Window.png)

### Animator
```Animator``` merupakan komponen yang digunakan untuk mengkontrol state animasi dari variable parameter - parameter. Dalam komponen ```Animator``` kita akan memberi asset bernama ```Animation Controller```. ```Animation Controller``` merupakan asset yang bertugas memberi tahu bagaimana komponen mengkontrol state animasinya.

![img](img/Animator-How-It-Work.png)

Untuk membuat suatu animasi, pertama kita harus menambahkan komponen ```Animator``` ke game object yang mau kita animasikan. Dalam project ini kita akan menambahkannya ke object Player.

![img](img/Animator-Component.png)

Dapat dilihat ada beberapa attribute dalam komponen tersebut. Untuk saat ini yang kita mau fokuskan adalah attribut ```Controller```. Selanjutnya kita buat ```Animation Controller``` asset. Sebelum itu kita buat folder bernama "Animation" untuk menyimpan semua asset mengenai animasi. Dalam folder "Animation" buatlah folder "Player" agar semua asset animasi player dapat kita taruh dalam folder "Player".

Masuklah ke folder "Player" dan klik kanan lalu pilih Create > Animation Controller.

![img](img/Create-Animation-Controller.png)

Beri nama "Player" lalu tekan enter. Drag and drop asset tersebut ke attribute Controller di komponen ```Animator```.

![img](img/Animator-Component-Controller-Assigned.png)

Dengan ini kita bisa melihat Window Animator akan mempunyai tampilan seperti berikut saat kita menselect game object dengan komponen Animator.

![img](img/Animator-Window-Empty.png)

Berikut adalah scheme sprite sheet.

![img](img/Animation-Scheme.png)

Dapat dilihat dari skema animasi tersebut, akan dibutuhkan 6 state.

Untuk membuat state kita dapat klik kanan di area state yang ada di window Animator lalu pilih Create-State > Empty. Tekan state yang sudah dibuat lalu beri nama menggunakan inspector. Buatlah 6 state sesuai dengan nama berikut.

![img](img/Animator-Window-Full-No-Link.png)

Dapat dilihat, akan ada minimal satu state yang tersambung dengan state Entry. State yang tersambung dengan state entry adalah state yang pertama kali dimasuki oleh Animator Controller.

Selanjutnya kita buat variable untuk parameter Animator. Untuk membuat parameter, klik simbol tambah di sisi atas kanan panel kiri. Disini kita dapat membuat beberapa jenis variable. Untuk ini, kita ingin variabel bool untuk IsUp, IsRunning, IsShooting. Buatlah 2 variabel tersebut. 

Setelah itu buat transisi antar state Idle ke run dengan klik kanan di state Idle, lalu pilih Make Transition selanjutnya klik ke Run. Dengan ini akan ada transisi. Jika garis panah yang menghubungkan kedua state, kita bisa mengubah beberapa atribute.

![img](img/Animation-Transition-Setting.png)

Disini, yang mau kita ubah adalah Has Exit Time, Transition Duration, dan Conditions. Has Exit Time berarti animasi akan berganti setelah kondisi terpenuhi dan mencapai exit time tertentu. Ini kita uncheck agar animasi langsung berubah setelah kondisinya tercapai. Transition duration adalah durasi sebelum animasi melakukan transisi ke animasi selanjutnya. Pada 3D animation ini akan memberikan inbetween frame. Sayangnya pada animation frame based tidak akan merubah apapun dan hanya memberikan delay sebelum animasi berubah. Maka kita beri 0 juga. Yang terakhir merupakan Kondisi, dimana kita dapat memberikan kondisi kapan transisi ini akan aktif. Jika kita memberikan lebih dari satu kondisi maka untuk transisi aktif semua kondisi tersebut harus benar.

Note : Untuk state A dan B kita bisa memberikan lebih dari satu transisi. Jadi pada transisi 1 dan yang lainnya akan berfungsi sebagai OR.

Buatlah transisi dengan kondisi seperti berikut dan settingan has exit dan transision duration sama.

1. Idle -> Run : IsRunning == True, IsShooting == False
2. Idle -> Shoot : IsShooting == True
3. Run -> Idle : IsRunning == False, IsShooting == False
4. Run -> Shoot : IsShooting == True
5. Shoot -> Run : IsShooting == False, IsRunning == True
6. Shoot -> Idle : IsShotting == False, IsRunning == False
7. Any -> IdleUp : IsUp == true

### Animation

## Reference
https://docs.unity3d.com/Manual/class-Tilemap.html
