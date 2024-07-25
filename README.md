# docker-laravel
This repository helps you set up your Laravel projects using Docker, even if you are not familiar with Docker.

## Services list
* laravel app
* nginx web server
* mysql database
## Setup

### 1. Clone the repository

first, clone the repository:

```bash
git clone https://github.com/devsoli/docker-laravel.git
cd docker-laravel
```
### 2. Create the environment file
copy the .env.example file to .env:
```bash
cp .env.example .env
```
config database connection in **.env** file:
```dotenv
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=password
```
### 3. Build app service
```bash
docker-compose build app
```
### 4. Run Docker Compose
to start the services, run:
```bash
docker-compose up -d
```
This command will run the Docker containers in the background.
### 5. Install dependencies
Enter the app container and install Composer dependencies:
```bash
docker-compose exec app composer install
```
### 6. Set the application key
Set the application key:
```bash
docker-compose exec app php artisan key:generate
```
### 7. Migrate the database
Migrate the database:
```bash
docker-compose exec app php artisan migrate
```
### 7. Access the application
After successfully running the above commands, your Laravel application should be accessible at http://localhost.

## Useful commands
* **View logs:**
```bash
docker-compose logs -f
```
* **Stop services:**
```bash
docker-compose down
```
* **Access the container:**
```bash
docker-compose exec app bash
```

## Common issues
* **Ports are already in use:** Make sure that ports 80 and 3306 are not being used by another service.
* **Permissions:** If you encounter file permission issues, try the following commands:
```bash
sudo chown -R $USER:$USER .
```
If you encounter any issues or have any questions, please open a new issue in the Issues section.
___
I hope this guide helps you easily set up your Laravel projects with Docker.