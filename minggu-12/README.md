
# Laporan, Latihan dan Tugas Praktikum Teknologi Cloud Computing - Minggu 12 
#### devia wisnu raharjo
##### 215411116


Langkah - langkah Praktikum

Section 2

### Configure Swarm Mode

#### Step 2. Menjalankan berbagai hal secara manual pada satu host dan membuat wadah baru di node1 dengan menjalankan

Login Docker : run

    $ docker run -dt ubuntu sleep infinity
   

melihat info docker

    $ docker ps


#### Step 2.1 - Create a Manager node

#### Inisialisasi New Swarm

   $ docker swarm init --advertise-addr $(hostname -i)
   $ docker info


#### Step 2.2 - Join Worker nodes to the Swarm

	Paste On Node 1 and Node 2

    $ docker swarm join --token SWMTKN-1-4jyeeeomwfddfbrhwib18kq08m7xisto1l0m3i5n8gpxbj1qy1-a6tizbli7zy4lm9nskm4ulhcw 192.168.0.18:2377
    $ docker node ls

#### Section 3: Deploy applications across multiple hosts
#### Step 3.1 - Deploy the application components as Docker services

    $ docker service create --name sleep-app ubuntu sleep infinity
    $ docker service ls

#### Section 4: Scale the application

    $ docker service update --replicas 7 sleep-app

    $ docker service ps sleep-app

    $ docker service update --replicas 4 sleep-app

    $ docker service ps sleep-app

#### Section 5: Drain a node and reschedule the containers

    $ cat Dockerfile

    $ docker node ls
