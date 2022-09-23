# 0. server 1cpu 2mem (exporter, promehteus, grafana) 

definisi
Ansible merupakan salah satu alat open source yang digunakan untuk mengotomasi proses setup yang dilakukan secara berulang pada banyak server menjadi sekali proses saja.

monitoring adalah program dimana mengvisualissasikan performa atau kinerja dari suatu server menjadi layanan visual.


Pertama sebelum kita melakukan monitoring kita membuat server terlebih dahulu, disin saya menggunakan satu server saja 

![img](assets/0.buat-server.png)


# 1. Install Ansible

![img](assets/ansi1.png)



![img](assets/ansi3.png)


![img](assets/ansible3.png)



# 2. Create user dengan nama kalian

![img](assets/ansi5.png)


# 3. install nginx and Docker using ansible


![img](assets/ansible4.png)

![img](assets/ansible5.png)


![img](assets/ansi4.1.png)


![img](assets/ansi7.png)


# 4. Install Monitoring using ansible on top docker

![img](assets/ansi9.png)




# 5. challange (monitoring specific container)

![img](assets/5.1.png)

```
sudo docker run -d -p 8083:8083 -p 8086:8086 --expose 8090 --expose 8099 --name influxsrv tutum/influxdb

```
```
sudo docker run --volume=/:/rootfs:ro --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8080:8080 --detach=true --link influxsrv:influxsrv --name=cadvisor google/cadvisor:latest -storage_driver_db=influxdb -storage_driver_host=influxsrv:8086
```

```
sudo docker run -d -p 3000:3000 -e INFLUXDB_HOST=localhost -e INFLUXDB_PORT=8086 -e INFLUXDB_NAME=cadvisor -e INFLUXDB_USER=root -e INFLUXDB_PASS=root --link influxsrv:influxsrv --name grafana grafana/grafana

```

![img](assets/5.2.png)


untuk mengecek apakah sudah run apa blom

```
docker ps -a
```

# 6. make reverse proxy with ansible 


![img](assets/reversenode.png)


![img](assets/reverseprom.png)


![img](assets/reversegrafana.png)


![img](assets/ansi10.png)



   # - node-exporter.name.studentdumbways.my.id (node exporter)

![img](assets/moninode.png)


   # - prometheus.ziq.studentdumbways.my.id (promehteus)

![img](assets/moniprome.png)

  
   # - dashboard.ziq.studentdumbways.my.id  (grafana)


![img](assets/monitorgrafana.png)

