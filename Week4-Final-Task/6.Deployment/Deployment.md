Set up semua app ke dalam docker kemudian congigurasikan


integrasi bagian api di fe


![img](assets/config-api.png)



RUNNING APP

Dockerfile >> docker-compose.yml >> Jenkinsfile

docker file 

![img](assets/depfe1.png)
![img](assets/depbe2.png)

```
docker build -t <customnama> .
```


![img](assets/depbe1.png)
![img](assets/depbe2.png)



```
docker compose up -d
```

semuanya di compose dan running container integrasi ke database agar bisa login 

ini hasilnya sudah di reverse proxy ssl


![img](assets/dep1.png)


![img](assets/dep2.png)

![img](assets/depploy1.png)


ok done