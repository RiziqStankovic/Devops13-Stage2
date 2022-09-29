# Setup PostgreSQL with Docker

Pertama kita pindah dlu branch ke production

![img](assets/switchbranch.png)

disini saya akan memasangnya menggunakan ansible biar lebih cepat dan mudah

cek ping dlu

![img](assets/cek-ping.png)



```
 - hosts: 'app'
   gather_facts: yes
   tasks:
    - name: Start Docker Service in server
      service:
        name: docker
        state: started
        # restart aja dlu

    - name: Install pip python3 dependencies 
      shell: sudo apt install python3-docker -y
 
    - name: Create Postgressql Container
      docker_container:
        name: postgres
        image: postgres:alpine3.16
        state: started
        recreate: yes
        ports:
          - "5432:5432"
        volumes:
          - /home/ziq/hitch_postgres_data:/var/lib/postgresql/data
        env:
          POSTGRES_USER: "admin"
          POSTGRES_PASSWORD: "@Arima01"
```


![img](assets/runpostgree.png)

![img](assets/logsuces.png)


kemmudian kita configurasikan 


![img](assets/config.png)

lalu kita migrasikan dan koneksikan kedalam database 

![img](assets/migrate.png)

![img](assets/createfbuser.png)

![img](assets/db1.png)

![img](assets/dbnew1.png)


![img](assets/psql1.png)


kita runing di client untuk mengeceknya 

install psql client nya

```
sudo apt install postgresql-client
```

![img](assets/psqlclient.png)

with command

```
psql -h iphost -p 5432 -d namadatabase -U nameusernnya
```

![img](assets/pdqlclient2.png)

oke done