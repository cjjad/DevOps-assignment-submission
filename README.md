# DevOps Assignment submission - Dockerized Laravel Application

This repository contains a Dockerized Laravel application for production purposes.

## Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/cjjad/DevOps-assignment-submission.git
   cd DevOps-assignment-submission
   ```

2. setup .env file
- rename the file named .env.example to .env and change this part lines of file:

    ```
    APP_NAME=Laravel
    APP_ENV=production
    APP_KEY=base64:uFHOe8UDV0IMmh4N20SWhmWLil+z6HpTDexrhLHemFY=
    APP_DEBUG=true
    APP_TIMEZONE=UTC
    APP_URL=http://localhost

    ...

    DB_CONNECTION=mysql
    DB_HOST=mysql
    DB_PORT=3306
    DB_DATABASE=laravel
    DB_USERNAME=root
    DB_PASSWORD=secret
    ```

3. start all containers with docker compose
    ```bash
    docker compose up -d
    ```

4. set folder permissions
    ```bash
    docker compose exec app chown -R www-data:www-data /app/storage
    docker compose exec app chmod -R 775 /app/storage
    ```

5. generate key for laravel app
    ```bash
    docker-compose exec app php artisan key:generate
    ```

6. migrate database
    ```bash
    docker compose exec app php artisan migrate --force
    ```

## Final result
now you can open http://localhost to view result of project