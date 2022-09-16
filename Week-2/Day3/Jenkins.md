
# 1. Install Jenkins on top docker (ssh agent plugin) ,(settup ssh key di dalam credential)

![img](assets/j1.png)
![img](assets/j2.png)
![img](assets/j5.png)
![img](assets/j7.png)
![img](assets/j8.png)
![img](assets/jgit.png)
![img](assets/jok.png)


# 2. Create script for cicd (git pull --> build --> jalankan --> push images ke registry) untuk frontend dan backend

# Jenkinsfile fe

![img](assets/j2.1.png)

# Jenkinsfile be

![img](assets/j2.2.png)

kemudian kita push ke repo kita untuk bisa di baca oleh om jenkins

![img](assets/ssgit.png)

# Deploy CI/CD fe

![img](assets/fejenkinscu.png)

# Deploy CI/CD be

![img](assets/jensucces.png)


# 3. Reverse proxy Jenkins jenkins.kelompok5.studentdumbways.my.id

Configurasi Reverse Proxynya di Server Nginx

![img](assets/revprox.png)


# 4. Pasang Webhook kedalam repository github kalian (url/github-webhook)

Configurasi Webhook dengan discord di setting-gitrep/webhook add webhook kmudian dapatkan url di discord

buat channel kita sendiri kmudian lakukan integrasi di bgian setting channelnya lalu copy dan paste di url git repo nya.

![img](assets/dcgit.png)


![img](assets/dcgit2.png)

gmabar Git di Phone

![img](assets/git.jpeg)


# 5. Jenkins Job Notification (slack, discord, telegram)

cara ini cukup simple kita tinggal menanbahkan script stage di dalam Jenkinsfile dari genererate syntax jenkins yang terdapat url dari discord untuk bisa mengirimakan notif, sebelumnya  kita install pugi terlebih dahulu khusus untuk discord kmudian lgusng kita edit file jenkins nya

![img](assets/dcjen.png)

lansung deploy

![img](assets/discord.png)

ss Di phone 

![img](assets/jen.jpeg)



