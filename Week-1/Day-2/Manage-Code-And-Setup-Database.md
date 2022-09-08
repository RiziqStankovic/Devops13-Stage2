# Membuat server backend dan database menggunakan [IdCloudhost](https://console.idcloudhost.com/hub/login)

- Membuat Server di IDCH 

![1](assets/1.0.png)
![1](assets/1.1.png)
![1](assets/1.3.png)
![1](assets/1.4.png)

# 1. Setup ssh key antar server
# Generate SSH key and transfer ke smua ssh server

![1](assets/1.5.png)

- masuk ke direktori ssh trus copy manual

![1](assets/1.7.png)

- Langsung copas

![1](assets/1.8.png)

- atau juga bisa menggunakan ssh-copy-id user@ip

![1](assets/2.0.png)

# Meremote ssh menggunnakan scp

- Bisa juga menggunakan scp

![1](assets/100.png)
```
scp -r .ssh user@ip:/
```
![1](assets/1.6.png)
![1](assets/101.png)



# 2. installation database mysql/mariadb 

![1](assets/103.png)
<!-- ![1](assets/104.png)
![1](assets/105.png) -->

# Manage DataBase MYSQL 
# 3. setup database , make user, privileges
![1](assets/106.png)
<!-- ![1](assets/107.png) -->
![1](assets/110.png)
<!-- ![1](assets/112.png) -->
![1](assets/113.png)


# Install MYSQL-Client

- Sebelum instal mysql client configurasi mysqld terlebih dahulu untuk bisa bind ke jaringan lain

![1](assets/bind.png)
![1](assets/mysqld-sconf.png)

![1](assets/mysql-client.png)
![1](assets/mysql-client2.png)

# 4. setup app backend (integration to database, reverse prxy, and multilevel domain )

<!-- ![1](assets/cloudflare.png) -->
![1](assets/4.1.png)


# Migrate DataBase

![1](assets/install-sequelize.png)
![1](assets/config-json.png)
![1](assets/db-migrate.png)
![1](assets/db-migrate2.png)


# 5. integration frontend application with backend application (sampai bisa melakukan registrasi)

![1](assets/4.2.png)
![1](assets/4.3.png)
![1](assets/4.4.png)
![1](assets/4.4.1.png)
![1](assets/4.5.png)
![1](assets/4.6.png)
![1](assets/4.7.png)

<!-- ![1](assets/register.png) -->

![1](assets/5.1.png)
![1](assets/5.2.png)

![1](assets/117.png) 











