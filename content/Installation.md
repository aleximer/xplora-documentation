## Manual
```
git clone git@bitbucket.org:xploranose/xplora-unified-activation.git
cd web
# Copy .env file from ftp://xploramobile.com/srv/dev/xua/
# Create database
# Change DB credentials in .env file to point to your database
composer install
npm i
npm run dev
php artisan key:generate
php artisan migrate:fresh --seed
php artisan serve
open http://127.0.0.1:8000
```
## Local (on Flywheel)

Create a new site with default settings, choose whatever you want for login a password. We're going to delete WordPress installation anyway.


> [!WARNING] PHP versions
> Branches `xploramoblie` and `laravel-7` work on the server with [[Xplora unified activation platform#^9a8e35|version 7.2]] 
> 
> If you have composer or compatibility problems choose PHP version 7 (7.4.30 or 7.3.5) when installing. You can switch later if you have site already set up:
> 
> ![[CleanShot 2024-02-04 at 19.33.00.png]]


![[CleanShot 2024-02-02 at 11.48.44.png]]

Wait when site has finished installing and open site shell

![[CleanShot 2024-02-02 at 11.52.19.png]]

Run following commands from there:

```
# Clone xua repository
cd app
git clone git@bitbucket.org:xploranose/xplora-unified-activation.git
cd ..

# Remove WordPress installation and link XUA public folder to app/public
rm -rf app/public
ln  -s "$(pwd)/app/xplora-unified-activation/web/public/" "/$(pwd)/app/"

## Setup Laravel application
cd app/xplora-unified-activation/web
composer install
npm i
npm run dev

```
Copy `app/xplora-unified-activation/web/.env.example` to `app/xplora-unified-activation/web/.env` and open it with the editor of your choice.

Change database values there:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=local
DB_USERNAME=root
DB_PASSWORD=root
DB_SOCKET=/Users/banana/Library/Application Support/Local/run/T_hAlVvP9/mysql/mysqld.sock
```

> [!WARNING] Change DB_SOCKET value to yours!
> You can get `DB_SOCKET` value from `Local -> Site -> Database -> Socket`
> 
> ![[CleanShot 2024-02-02 at 12.13.00.png]]

```
# Run Laravel specific commands and DB migrations
php artisan key:generate
php artisan migrate:fresh --seed
php artisan cache:clear
```

> [!WARNING] Use [[Xplora unified activation platform#Branches]] for development
> `master` branch is not the main branch to work with

> [!TIP] You can set `APP_URL` value in `.env` file to reflect domain in Local
> It will help Laravel to generate correct links in CLI

