
# Laporan, Latihan dan Tugas Praktikum Teknologi Cloud Computing - Minggu 9 
#### devia wisnu raharjo
##### 215411116



## Pembahasan

Dalam praktikum ini ada beberapa tahapan diantaranya adalah :

## Task 0: Prerequisites

1. Prerequisites (kita melakukan clone linux_tweet_app ) terlebih dahulu.
   Persiapan DOCKERID jika belum memiliki akun docker wajib mendaftar dan membuat DOCKERID terlebih dahulu.
	Hasilnya 

    $ git clone https://github.com/dockersamples/linux_tweet_app
	

## Task 1: Run some simple Docker containers

2. Selanjut "Run some simple Docker containers" untuk menjalankan ini bisa berupa script shell atau aplikasi khusus, dan terkoneksi dengan container mirip seperti penggunaan remote SSH yang berguna untuk layanan jangka panjang seperti database dan website.

	Jalankan perintah di linux :
    $ docker container run alpine hostname
	

3. Menampilkan list container dimana docker menjaga container tetap berjalan pada saat proses dalam container sedang berjalan.
	Jalankan perintah dibawah untuk melihat seluruh container yang sedang berjalan :
	
    $ docker container ls --all
	

4. Menjalankan container berdasarkan Versi Linux dari masing - masing Docker host, pada praktik ini menjalankan Container Linux diatas Host Alpine Ubuntu untuk tiap node nya. 
	Berikut perintahnya untuk menjalankan container Docker dan mengakses shellnya.
	
    $ docker container run --interactive --tty --rm ubuntu bash
	

	Sedikit penjelasan script diatas : 
	--interactive untuk melakukan interkoneksi atau interaksi.
	--tty mengalokasi pseudo-tty.
	--rm perintah ini akan memberi informasi Docker untuk melanjutkan proses dan menghapus container setelah selesai dijalankan.

5. Kemudian menjalankan perintah dibawah didalam container :
    
    $ ls /
	menampilkan isi data root folder pada container
    $ ps aux
	menampilkan proses berjalan dalam container
    $ cat /etc/issue
	akan menampilkan distro linux apa yang dijalankan oleh container, dalam hal ini Ubuntu 22.04 LTS
	
6. Perintah exit untuk keluar dari sesi shell dan menghentikan proses bash dan container keluar.
    
    $ exit

7. Kemudian untuk mengecek versi host virtual machine ketikan perintah :
   
   $ cat /etc/issue
	
8. Menjalankan MySql Container dengan perintah dibawah ini :
    
    $ docker container run \
 	--detach \
 	--name mydb \
 	-e MYSQL_ROOT_PASSWORD=my-secret-pw \
 	mysql:latest
	#### Penjelasan Script ####
	--detach untuk menjalankan 
 	--name mydb nama database ### mydb ###
 	-e untuk menetukan environment variabel password


9. Menampilkan Container yang sedang berjalan dengan perintah :
    
    $ docker container ls
	
10. Kita dapat mengecek apa saja yang terjadi di container menggunakan perintah :
    
    $ docker container logs mydb
	
	
11. Melihat versi MySql menggunakan perintah :
    
    $ docker exec -it mydb \
	mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version
	 

12. Kita dapat menggunakan container exec untuk mengkoneksikan dan membuat proses baru di baris shell container yang sedang berjalan.
    
    $  docker exec -it mydb sh

13. Selanjutnya kita cek MySql versi kemudian keluar dari proses menggunakan perintah :

    $ mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version
    $ exit

## Task 2: Package and run a custom app using Docker

14. Selanjutnya kita akan mencoba membuat dan menjalankan sebuah aplikasi menggunakan Dockerfile. 
Sebelumnya kita pastikan berada di dalam direktori linux_tweet_app dengan perintah :
    
    $  cd ~/linux_tweet_app
	Menampilkan isi dari Dockerfile 
    $ cat Dockerfile
	 


15. Selanjutnya kita menggunakan docker image build untuk membuat Docker Image baru dalam Dockerfile :
    Sebelumnya kita lakukan langkah untuk mengexport DOCKERID kita, disini saya export DOCKERID=bondanproject/myrepo_9
    
    $ export DOCKERID=bondanproject/myrepo_9
    
    $  cat Dockerfile
    
    $  echo $DOCKERID
    
bondanproject/myrepo_9

    $ docker image build --tag $DOCKERID/linux_tweet_app:1.0 .
    
    Selengkapnya ada pada gambar dibawah ini :
    

16. Selanjutnya kita menggunakan docker container run untuk memulai container baru dari image yang dibuat :

    $ docker container run \
	--detach \
 	--publish 80:80 \
 	--name linux_tweet_app \
 	$DOCKERID/linux_tweet_app:1.0
	Kemudian akses website :


## Task 3: Modify a running website

17. Disini kita akan merubah dan sedikit memodifikasi tampilan web menggunakan mount :

    $ cp index-new.html index.html


18. Update Images :
    $ docker image build --tag $DOCKERID/linux_tweet_app:2.0 .
    
    $ docker image ls


19. Push Images to Docker HUB
    List Images Docker Host
    
    $ docker image ls -f reference="$DOCKERID/*"


20. Docker Login :
    $ docker login


21. Push Images to DockerHub

   $ docker image push $DOCKERID/linux_tweet_app:1.0
   

   $ docker image push $DOCKERID/linux_tweet_app:2.0
   



```

