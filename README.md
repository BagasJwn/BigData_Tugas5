## Bigdata 2020


# Tools
Dari tugas ini kita membutuhkan beberapa tools yang digunakan:
1. Docker Desktop( dengan syarat spesifikasi windows 10 pro jika di install di windows)
2. Apache Spark

# Install
- yang pertama install docker dari web yang tertera https://www.docker.com/
- melakukan intruksi dari Apache Spark dari Bitnami

# Tugas
- Jumlah worker 2,5
- Jumlah CPU: 2, 4
- Memory: 1G
- Partisi: 100, 1000

Untuk menambahkan worker, memodifikasi jumlah CPU dan memory, kalian bisa mengcopy file<br/> 
docker-compose.yml dan memodifikasi sesuai kebutuhan.

Dokumentasikan percobaan kalian dengan baik dan buatlah kesimpulan dari hasil percobaan <br/>
tersebut.

# 2 worker
- sebelumnya pastikan docker desktop sudah terinstall.<br/>

- masuk ke halaman yang terdapat file yml.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step1.PNG "docker")<br/>

```version: '2'

services:
  spark:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=master
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
    ports:
      - '8080:8080'
  spark-worker-1:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
  spark-worker-2:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
 
```

- jalankan yml untuk menjalankan worker. dengan syntax ``` docker-compose up -d ```<br/>

- mengecek di ui.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step1_a.PNG "docker")<br/>

- masuk di cmder dengan syntax dengan syntax ``` docker ps ```.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step2_a.PNG "docker")<br/>

- eksekusi id container dengan menggunakan ``` docker exec -it <container_id> /bin/bash ```.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step6_a.PNG "docker")<br/>

- cek nama alamat hostname dengan syntax ini ``` hostname -i ```.<br/>

- jalankan syntax ini dengan mengatur partisi yang diperintahkan<br/>
```  park-submit --master spark://172.26.0.2:7077 examples/src/main/python/pi.py 10 ```.<br/>

1. partisi 100 menjalankan syntax dengan yang menjalankan syntax dibawah<br/>
disesuaikan dengan alamat yang ada<br/>
```  park-submit --master spark://172.26.0.2:7077 examples/src/main/python/pi.py 100 ```.<br/>

- eksekusi akan menghasilkan nilai pi seperti yang ada di bawah.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step10_a_bukti.PNG "docker")<br/>


- serta jangan lupa mengecek di ui apache spark.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step10_a.PNG "docker")<br/>

2. partisi 1000 menjalankan syntax dengan yang menjalankan syntax dibawah<br/>
disesuaikan dengan alamat yang ada<br/>
```  park-submit --master spark://172.26.0.2:7077 examples/src/main/python/pi.py 1000 ```.<br/>

- eksekusi akan menghasilkan nilai pi seperti yang ada di bawah.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step11_a_bukti.PNG "docker")<br/>


- serta jangan lupa mengecek di ui apache spark.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step11_a.PNG "docker")<br/>

# 5 worker
- masuk ke halaman yang terdapat file yml.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step1.PNG "docker")<br/>

```version: '2'

services:
  spark:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=master
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
    ports:
      - '8080:8080'
  spark-worker-1:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
  spark-worker-2:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
  spark-worker-3:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
  spark-worker-4:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no
  spark-worker-5:
    image: bitnami/spark:2
    environment:
      - SPARK_MODE=worker
      - SPARK_MASTER_URL=spark://spark:7077
      - SPARK_WORKER_MEMORY=1G
      - SPARK_WORKER_CORES=1
      - SPARK_RPC_AUTHENTICATION_ENABLED=no
      - SPARK_RPC_ENCRYPTION_ENABLED=no
      - SPARK_LOCAL_STORAGE_ENCRYPTION_ENABLED=no
      - SPARK_SSL_ENABLED=no

```

- jalankan yml untuk menjalankan worker. dengan syntax ``` docker-compose up -d ```<br/>

- mengecek di ui.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step3_bukti5.PNG "docker")<br/>

- masuk di cmder dengan syntax dengan syntax ``` docker ps ```.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step2.PNG "docker")<br/>

- eksekusi id container dengan menggunakan ``` docker exec -it <container_id> /bin/bash ```.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step6.PNG "docker")<br/>

- cek nama alamat hostname dengan syntax ini ``` hostname -i ```.<br/>

- jalankan syntax ini dengan mengatur partisi yang diperintahkan<br/>
```  park-submit --master spark://172.25.0.6:7077 examples/src/main/python/pi.py 10 ```.<br/>

1. partisi 100 menjalankan syntax dengan yang menjalankan syntax dibawah<br/>
disesuaikan dengan alamat yang ada<br/>
```  park-submit --master spark://172.25.0.6:7077 examples/src/main/python/pi.py 100 ```.<br/>

- eksekusi akan menghasilkan nilai pi seperti yang ada di bawah.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step10_bukti.PNG "docker")<br/>


- serta jangan lupa mengecek di ui apache spark.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step10.PNG "docker")<br/>

2. partisi 1000 menjalankan syntax dengan yang menjalankan syntax dibawah<br/>
disesuaikan dengan alamat yang ada<br/>
```  park-submit --master spark://172.25.0.6:7077 examples/src/main/python/pi.py 1000 ```.<br/>

- eksekusi akan menghasilkan nilai pi seperti yang ada di bawah.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step11_bukti.PNG "docker")<br/>


- serta jangan lupa mengecek di ui apache spark.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_5/picture/step11.PNG "docker")<br/>




