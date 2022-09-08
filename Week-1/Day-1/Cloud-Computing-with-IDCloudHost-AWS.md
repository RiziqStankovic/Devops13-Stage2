![1](assets/1-Cloud-Computing.webp)

Secara konsep, definisi Cloud Computing berarti menyimpan dan mengakses data dan program melalui internet dari lokasi berbeda dimanapun berada asalkan terhubung dengan jaringan internet sehingga bisa di kelola oleh device(Computer, SmartPhone) menuju hard drive yang tersimpan.

# Membuat Server Gateway dan Aplikasi menggunakan IdCloudhost & AWS

![image](https://user-images.githubusercontent.com/106061407/172402771-cd9fbf3b-6ac8-4cc1-855a-854136475b32.png)
![2](assets/aws.png)

PT Cloud Hosting Indonesia (IDCloudHost) Merupakan Salah Satu Web Hosting Provider yang Ada di Indonesia dengan Menawarkan Layanan Seperti Pendaftaran Domain, Cloud Hosting, Server (VPS & Dedicated Server), Reseller Domain & Hosting, dan Beberapa Fitur Layanan Lainnya.

Langkah Pertama sebelum membuat server gateway terlebih dahulu harus membuat server itu sendiri dimana kita menggunakan Virtual Privat Server atau bisa juga disebut dengan VPS di IDCloudHost 
Klik Link [ini](https://idcloudhost.com/) untuk membuat akun nya kemudian login sebagai console 

 ![3](assets/3.png)

    - silahkan login or Sign In jika blom punya akun
 
 ![4](assets/4.png)



 ![5](assets/5.png)

    - Trus CONFIGURASI VPS nya 

 ![6](assets/6.png)

 ![7](assets/7.png)

 ![8](assets/8.png)

 ![8](assets/9.png)
 
    - klo sudah silahkan integrasikan ke terminal dengan perintah
```
ssh nameserver@IP-PUBLIC
```

 ![10](assets/10.png)

atau juga bisa membuatnya di platform luar indonesia yaitu AWS klik link [ini](https://aws.amazon.com/id/) untuk membuat akunya dengan menggunakan server CE2, VPS sama halnya dengan di IDCloudHost.

![1](assets/aws1.png)

    - pergi navbar kiri lalu klik instans
![2](assets/aws2.png)

    - kemudian Luncurkan Intens Membuat Server
![3](assets/aws3.png)

    - IKUTI langkah Berikut 

![2](assets/aws4.png)

    - 1

![2](assets/aws5.png)

    - 2

![2](assets/aws6.png)

    - 3

![2](assets/aws7.png)

    - 4

![2](assets/aws8.png)

    - 5

![2](assets/aws9.png)

    - 6

![2](assets/aws10.png)

    - 7 Kemudian Hubungkan Ke cmd Melalui Command line di aws

![2](assets/aws11.png)

    - 8 Hubungakn dengan file format .pem berada
![2](assets/aws12.png)

    - 9 jika selesai Terhubung sperti PIC di bawah 

![2](assets/aws13.png)

    - kemudian langsung install gateway nya

![2](assets/1.1.png)
```
sudo apt update ; sudo apt upgrade
```
```
sudo apt install nginx
```


![2](assets/1.2.png)

    - nginx -v

    - kemudian configurasi ke nginx.conf 

![2](assets/1.3.png)

    - buat direktori khusus untuk menampung domain

![2](assets/1.4.png)

    - tambhkan include /etc/nginx/dumbways/*; menggunkan format * untuk mengeksekusi smuanya dlm folder


![2](assets/1.4.1.png)
```
sudo nginx -t
```

    - untuk memeriksa test fail

# Install Aplikasi

![2](assets/1.5.png)

    - masukan configurasi ip applikasi untuk di sambungkan ke gateway

![2](assets/1.6.png)

    - kemudian install aplikasi nya di server berbeda

    - disini saya menggunakan aws dan juga idch tapi saya tulis menggunkan idch 
```
git clone https://github.com/dumbwaysdev/wayshub-frontend
```

    - clone with github 
![2](assets/1.7.png)

    - instal npm nvm node
```
sudo apt install npm
```
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```
```
exec bash
```
```
nvm install 16
```
```
npm i
```


![2](assets/1.9.png)

```
npm install pm2 -g
```

![2](assets/1.9.1.png)

    - buat folder ecosystem di dalam folder
```
pm2 ecosystem simple
```

    - lakukan edit di file ecosystem
```
module.exports = {
  apps : [{
    name   : "frontend-wayshub",
    script : "npm start"
  }]
}
```

    -kemudian configurasi file js nya dan
```
pm2 start ecosystem.config.js
```

![2](assets/2.0.0.png)

    - cek di browser menggunkan ip 

![2](assets/way1.png)

# install domain dan ssl cert bot

![2](assets/way3.png)

    - configurasi domain dengan ip gateway public dan domain di direktori yang sama kmudian cek hasilnya udah ke konek ke domain or no

![2](assets/way2.png)

    - hasilnya udah konek but status masih not secure blom ada keamanan krna ssl blom di install 

![2](assets/ssl1.png)

    - langsung install certbot but jan lupa untuk restart nginx.service nya
```
sudo snap install core; sudo snap refresh core
```
```
sudo snap install --classic certbot
```
```
sudo certbot
```
![2](assets/ssl2.png)

    - ssl berhasil di iinstall pergi ke browser untuk melihatnya 
    
![2](assets/way4.png)



![2](assets/dumbflix1.png)















