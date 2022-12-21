
# Laporan, Latihan dan Tugas Praktikum Teknologi Cloud Computing - Minggu 10 
#### devia wisnu raharjo
##### 215411116


## Pembahasan

Dalam praktikum ini ada beberapa tahapan diantaranya adalah :

Section #1 - Networking Basics

Docker Network Command

      $ docker network


Daftar docker network

      $ docker network ls


Inspect a network

      $ docker network inspect bridge


Docker info

      $ docker info



Section #2 - Bridge Networking

daftar docker network 

      $ docker network ls



Selanjutnya kita mulai install dulu brctl dengan perintah 

      $ sudo apt-get install bridge-utils


      $ brctl show

menampilkan detail dari docker0

      $ ip a


Membuat container baru dengan menjalankan perintah :

      $ docker run -dt ubuntu sleep infinity

Memverivikasi container

      $ docker ps

Kembali kita tampilkan bridge-utils menggunakan 

      $ brctl show

kita inspect kembali menggunakan perintah 

      $ docker network inspect bridge

Lakukan ping dengan 172.17.0.2

      $ ping -c5 172.17.0.2

Docker ps

      $ docker ps

sekarang kita coba menjalankan didalam shell container ubuntu dengan perintah :

      $ docker exec -it fa39e102f0a4 /bin/bash


Selanjutnya kita install program ping dengan menjalankan perintah dibawah ini :

      $ apt-get update && apt-get install -y iputils-ping

selanjutnya kita coba koneksi dengan ping ke github

      $ ping -c5 www.github.com

Konfigurasi NAT untuk koneksi luar dengan memulai membuat container baru nginx

      $ docker run --name web1 -d -p 8080:80 nginx

      $ docker ps
      
kita buka web dengan durl 

      $ curl 127.0.0.1:8080

Section #3 - Overlay Networking
Cleaning Up

Pada langkah ini kita akan menginisialisasi swarm baru konek dengan node dan memverivikasinya.

Jalankan perintah berikut ini :

      $ docker swarm init --advertise-addr $(hostname -i)

Jalankan docker-swarm-join

      $ docker swarm join --token SWMTKN-1-28egcsrt15whmx4a5i9n6u3d7blnhip4bik468xm95l9kuuaxr-68l5e9lr62nyscynu9ui3ewym 192.168.0.27:2377

	$ docker node ls

Membuat jaringan overlay

	$ docker network create -d overlay overnet
	$ docker network ls


Jalankan juga di terminal kedua 
	
	$ docker network ls

Kita inspect overnet

	$ docker network inspect overnet

# Step 3 Saatnya membuat layanan menggunakan jaringan yang sudah terinisialisasi

	$ docker service create --name myservice \
	--network overnet \
	--replicas 2 \
	ubuntu sleep infinity	

	$ docker service ls


Memverifikasi single task (replika)

	$ docker service ps myservice


	$ docker network ls


	$ docker network inspect overnet


Test jaringan 

	$ docker network inspect overnet

	$ docker ps


install 
	
	$ docker exec -it e345aed47cba /bin/bash

	$ apt-get update && apt-get install -y iputils-ping


test ping 10.0.0.3

	$ ping 10.0.0.3 

	$ cat /etc/resolv.conf

ping myservice
	
	$ ping -c5 myservice

docker inspect myservice

	$ docker service inspect myservice

# cleaning up

	$ docker service rm myservice

	$ docker ps

	$ docker kill 3ae8a2ac8297

	$ docker swarm leave --force


	

