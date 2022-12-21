
# Latihan Praktikum Teknologi Cloud Computing - Minggu 8 
#### devia wisnu raharjo
##### 215411116


## Materi

**Docker Compose**
Docker compose digunakan untuk otomisasi proses - proses manual sebelumnya yang sudah kita buat (multi container dijalankan). 
Pertama kita buat file - file terlebih dahulu sesuai dengan arahan.


#### Install docker compose

    $ sudo install docker-compose

#### manualy install docker-compose

    $ DOCKER_CONFIG=${DOCKER_CONFIG:-$HOME/.docker}
    $ mkdir -p $DOCKER_CONFIG/cli-plugins
    $ curl -SL https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-linux-x86_64 -o $DOCKER_CONFIG/cli-plugins/docker-compose
    $ chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose


#### Membuat dirketori/folder project (composetest)

    $ mkdir composetest
    $ cd composetest

#### Membuat file app.py yang akan di panggil

	import time

	import redis
	from flask import Flask

	app = Flask(__name__)
	cache = redis.Redis(host='redis', port=6379)

	def get_hit_count():
    	retries = 5
    	while True:
        try:
            return cache.incr('hits')
        except redis.exceptions.ConnectionError as exc:
            if retries == 0:
                raise exc
            retries -= 1
            time.sleep(0.5)

	@app.route('/')
	def hello():
    	count = get_hit_count()
    	return 'Hello World! I have been seen {} times.\n'.format(count)
	


#### Membuat file lainnya yaitu requirements.txt yang akan di panggil
	
	$ nano requirments.txt

	flask
	redis


# Membuat file Docker / Dockerfile

#### Dockerfile berfungsi untuk membuild docker image dan bersii semua package/dependensi dari python bahkan python itu sendiri.
	$ nano Dockerfile (tanpa ekstensi apapun!)

di isi dengan code dibawah ini :

	# syntax=docker/dockerfile:1
	FROM python:3.7-alpine
	WORKDIR /code
	ENV FLASK_APP=app.py
	ENV FLASK_RUN_HOST=0.0.0.0
	RUN apk add --no-cache gcc musl-dev linux-headers
	COPY requirements.txt requirements.txt
	RUN pip install -r requirements.txt
	EXPOSE 5000
	COPY . .
	CMD ["flask", "run"]


#### Membuat file docker-compose.yml

	version: "3.9"
	services:
 	 web:
 	   build: .
 	   ports:
 	     - "8000:5000"
	 redis:
    	   image: "redis:alpine"

# Build and run app dengan docker compose

	$ docker compose up


#### stop docker compose yang sedang berjalan menggunakan Ctrl + C atau menggunakan perintah :

	$ docker compose down

# Edit Compose File menambahkan "bind mount" untuk web service untuk mempermudah pengelolaan volume pada container

	$ nano docker-compose.yml

	version: "3.9"
	services:
  	 web:
    	  build: .
    	  ports:
         - "8000:5000"
        volumes:
         - .:/code
        environment:
         FLASK_DEBUG: True
      redis:
        image: "redis:alpine" 
	

# Rebuild dan Run app with Compose
	$ docker compose up

(on proses maping volume)
