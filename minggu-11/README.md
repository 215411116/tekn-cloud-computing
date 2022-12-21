
# Laporan Praktikum Teknologi Cloud Computing - Minggu 11 
#### Devia Wisnu raharjo
##### 215411116


Langkah - langkah Praktikum

Stage Setup

Kita mulai dengan meng-kloning demo kode dari repository git.

    $ git clone https://github.com/ibnesayeed/linkextractor.git

    $ cd linkextractor
   
    $ git checkout demo
   

# Step 0: Basic Link Extractor Script

cek isi data step0

    $ git checkout step0
   
    $ tree

melihat isi dari file linkextractor.py

    $ cat linkextractor.py
   
Kita coba menjalankan script diatas 

    $ ./linkextractor.py http://example.com/

maka hasilnya error akses ditolak 

kita cek file linkextractor.py

    $ ls -l linkextractor.py

kita rubah permission menggunakan perintah 

    $ chmod a+x linkextractor.py
   
Run Python

    $ python3 linkextractor.py

# Step 1: Containerized Link Extractor Script

cek isi data step1

    $ git checkout step1

    $ tree

Cat Dockerfile

    $ cat Dockerfile

    $ sudo apt install python3-pip
    
selanjutnya kita install beautifulsoup4

    $ pip install beautifulsoup4

selanjutnya kita install pip requests (sudah tersedia di paket py3)

    $ pip install requests

selanjutnya kita membangun Docker Image dengan perintah dibawah ini 

    $ docker image build -t linkextractor:step1 .
menampilkan Docker Image dengan nama linsextractor:step1

    $ docker image ls
selanjutnya menjalankan satu container linkextractor:step1

    $ docker container run -it --rm linkextractor:step1 http://example.com/

menghasilkan tautan seperti dibawah ini :
selanjutnya mencoba lebih banyak link didalamnya dengan perintah 

    $ docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/
sebelum kita checkout step2 kita lakukan comit menggunakan perintah 

    $ git stash

# Step 2: Link Extractor Module with Full URL and Anchor Text

disini kita akan mencoba lebih banyak lagi, kita checkout step2

    $ git checkout step2
    $ tree
   
selanjutnya kita melihat skirp yang sudah update dari step2 ini 

    $ cat linkextractor.py

sekarang kita akan mencoba membangun docker image pada step2

    $ docker image build -t linkextractor:step2 .

    $ docker image ls

selanjutnya kita mencoba menjalankan container pada image step2 dengan perintah dibawah 

    $ docker container run -it --rm linkextractor:step2 https://training.play-with-docker.com/
kita juga  mencoba untuk menjalankan container step1

    $ docker container run -it --rm linkextractor:step1 https://training.play-with-docker.com/

Sampai dengan langkah kedua ini kita telah belajar dan mempelajari pengemasan script menggunakan dependensi yang dibutuhkan dengan lebih fleksibel, kita mempelajari membuat perubahan dalam aplikasi dan membuat berbagai varian docker image yang berada dalam satu wadah.

# Step 3: Link Extractor API Service

Pada langkah ini kita akan mencoba membangun dan menjalankan layanan web menggunakan script ini dalam docker.

    $ git checkout step3
    $ tree

Selanjutnya kita masuk dockerfile dengan perintah 

    $ cat Dockerfile

kita lihat isi main.py 

    $ cat main.py

selanjutnya kita build image dan jalankan docker container :

    $ docker image build -t linkextractor:step3 .
   
    $ docker container run -d -p 5000:5000 --name=linkextractor linkextractor:step3

    $ docker container ls
Selanjutnya membuat request HTTP dalam bentuk url

    $ curl -i http://localhost:5000/api/http://example.com/

setelah servis API berjalan dan mendapatkan respon JSON berupa Link url seperti pada gambar.

kita dapat melihat log menggunakan perintah :

    $ docker container logs linkextractor

kita mematikan dan menghapus container log setelah ditampilkan menggunakan perintah dibawah :

    $ docker container rm -f linkextractor

Step 4: Link Extractor API and Web Front End Services

Langkah selanjut membuat layanan GUI 

kita checkout dulu file step4

    $ git checkout step4
    $ tree
selanjutnya kita lihat file docker-compose.yml

    $ cat docker-compose.yml

kita lihat isi file index.php

    $ cat www/index.php

selanjut kita jalankan docker compose

    $ docker-compose up -d --build


pastikan bahwa keduanya layanan berjalan docker container 

    $ docker container ls
selanjutnya kita test service API

reloading

    $ sed -i 's/Link Extractor/Super Link Extractor/g' www/index.php

    $ git reset --hard

    $ docker-compose down
   

Step 5: Redis Service for Caching

    $ git checkout step5
    $ tree
 
kita tampilkan Dockerfile

    $ cat www/Dockerfile

kita tampilkan main.py

    $ cat api/main.py

selanjutnya kita tampilkan docker-compose.yml

    $ cat docker-compose.yml

kita booting dan up service

    $ docker-compose up -d --build

    $ docker-compose exec redis redis-cli monitor

    $ sed -i 's/Link Extractor/Super Link Extractor/g' www/index.php

    $ git reset --hard

    $ docker-compose down

# Step 6: Swap Python API Service with Ruby Conclusions

    $ git checkout step6
    
    $ tree

    $ cat api/linkextractor.rb

    $ cat api/Dockerfile

    $ cat docker-compose.yml


dalam ervice ii kita build dan jalankan docker-compose 

    $ docker-compose up -d --build 

Akses API dengan port baru 

    $ curl -i http://localhost:4567/api/http://example.com/

Sekarang kita lakukan shut-down terhadap compose

    $ docker-compose down

cek apakah log masih ada setelah service di matikan 

    $ cat logs/extraction.log

Sejauh ini, kita telah mempraktekan docker-compose untuk mengatur beberapa aplikasi berjalan dalam lingkup pengembangan.


