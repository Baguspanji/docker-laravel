# Docker - Laravel - MYSQL - PHP 8.0.13 

# Set enviropment
- copy `.env.example` menjadi `.env`.
- sesuaikan environment.
- jalankan docker composer dengan perintah 
```
docker-compose build app
```

# Menjalankan Docker
- jalankan docker composer dengan perintah 
```
docker-compose up -d app
```

# Menjalankan perintah php
- untuk menjalankan perintah php pada laravel bisa dengan 
```
docker-compose exec app php artisan ..
```
- untuk menjalankan perintah composer pada laravel bisa dengan 
```
docker-compose exec app composer require ..
```

# Masuk ke terminal Laravel
- atau anda dapat menjalankan perintah
- jalankan docker composer dengan perintah 
```
docker-compose exec app /bin/sh
```
- lalu anda dapat menjalankan perintah php seperti 
```
php artisan ..
```