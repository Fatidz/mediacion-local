
# Contenido

1. Instalaciones recomendadas 🔧
2. Como empezar con Laravel 🚀
3. Acceso a repositorio del PJ

## 1. Instalaciones recomendadas 🔧

Se recomienda instalar estas herramientas y en este orden

1.1. PHP & Apache
1.2. Composer
1.3. Git
1.4. MySQL (opcional)
1.5. Gestor de Base de datos
1.6. Docker (opcional)

### 1.1 PHP & Apache

- En Windows

    Se recomienda instalar XAMPP que es una distribucion que contiene Apache y PHP, e inclusive Mysql/MariaDB.
    La ultima version en esta pagina [Download XAMPP](https://www.apachefriends.org/es/download.html)
    Para buscar una version en especial, buscar [aquí](https://sourceforge.net/projects/xampp/files/)

- En Linux Ubuntu

    Ejectuar estos comandos en la terminal:

    Agregamos repositorio de php
    ```bash
    sudo add-apt-repository ppa:ondrej/php
    ```

    Actualizamos paquetes
    ```bash
    sudo apt-get update

    ```

    Instalamos php & apache
    ```bash

    sudo apt -y install php7.4

    ```

    Luego instalamos los principales modulos que nos servira para laravel
    ```bash

    sudo apt-get install -y php7.4-cli php7.4-json php7.4-common php7.4-mysql php7.4-zip php7.4-gd php7.4-mbstring php7.4-curl php7.4-xml php7.4-bcmath
    ```

### 1.2. Composer

Composer es el gestor de paquetes de PHP y nos servira para nuestros proyectos en Laravel

Descargar siguiendo las intrucciones de esta pagina: [Composer Download](https://getcomposer.org/download/).

- En Linux ubuntu

    Una vez descargado, renombrar y mover a la carpeta de binarios

    ```bash
        sudo mv composer.phar /usr/local/bin/composer
    ```

    Luego verificar si funciona:

    ```bash
        composer --version
    ```

### 1.3 Git

Importante para versionar nuestro codigo y trabajar en equipo!

- En Linux Ubuntu

    ```bash
        sudo apt-get install git-core
    ```

    ```bash
        git --version
    ```


    Luego de instalar y verificar, importante configura usuario y correo.
    ```bash
        git config --global user.name "Lionel Messi"
    ```

    ```bash
        git config --global user.email "<lio.messi@gmail.com>"
    ```

### 1.4 MySQL

Recomendable tener instalado esta base de datos para desarrollo, poder trabajar en forma local antes de meter tus cambios en la base de prueba o produccion

- En Linux Ubuntu
    ```bash
        sudo apt install mysql-server
    ```bash

    ```bash
        sudo mysql
    ```bash

### 1.5 Gestor de base de datos

Importante tener un gestor de base de datos para acceder a consultar datos, hacer cambios y pruebas

2 opciones muy recomendadas:

- Workbench para mySQL o MariaDB
- DBeaver para la mayoria de las BD del mercado (Postgres, ORacle, SQL Server, etc)

Workbench en Linux Ubuntu
    ```bash
        snap connect mysql-workbench-community:password-manager-service
    ```bash

Si usas KDE como gestor de ventanas, se recomienda instalar este paquete para no tener problemas de acceso:

    ```bash
        sudo apt install gnome-keyring
    ```


### 1.6 Docker

Otra instalacion recomendada es usar Docker. Donde puedes crear tus entornos de desarrollo y compartirlo en equipo para tener la misma configuracion en tus proyectos


Algunos contenedores que podrian ser utiles:

- PHP 5.6
    ```bash
        sudo docker pull hrquinones/myphp56:v01
    ```

- SQL Server 2017

    ```bash
        sudo docker pull mcr.microsoft.com/mssql/server:2017-GA-ubuntu
    ```

## 2. Como empezar con laravel 🚀

Para crear un proyecto laravel, se puede usar composer
Ejemplo comando

```bash
composer create-project --prefer-dist laravel/laravel nombre-proyecto "5.8.*"
```

Para crear un servicio Api rest, los pasos seria: crear el modelo,  tabla y controlador
lectura recomendada: [Laravel API Tutorial](https://www.toptal.com/laravel/restful-laravel-api-tutorial)

### 2.1 Crear modelo

Comando para crear un modelo:

```bash
    php artisan make:model Country
```

Se crea el archivo en /app

### 2.2 Crear tabla

El siguiente comando crea la plantilla para la estructura de la tabla en database/migrations
Se recomienda leer: https://laravel.com/docs/4.2/schema

```bash
    php artisan make:migration create_city_table
```

Para ejecutar el proceso de crear las tablas:

```bash
    php artisan migrate
```

Para insertar datos: se crea un archivo en la carpeta database/seeds
En este archivo se indica que datos insertar
Se recomienda leer: https://laravel.com/docs/4.2/migrations
El comando para crear archivo seeder

```bash
    php artisan make:seeder CountrySeeder
```

El comando para ejecutar el proceso para insertar datos:

```bash
    php artisan db:seed
```


### 2.3 Crear controlador

Comando para crear controlador

```bash
    php artisan make:controller CountryController
```

Se crea en app/Http/Controllers. Dentro se deben definir todas las acciones del api


### 2.4 Agregar endpoints al routes
Se debe agregar en routes/api.php para que sea accesible, con un nombre y una acción

Ejemplo:

```php
    use App\Http\Controllers\CountryController;

    Route::get('/countrys', [CountryController::class, 'list']);
    Route::get('/country/{id}', [CountryController::class, 'get']);
    Route::post('/country', [CountryController::class, 'post']);
    Route::put('/country/{id}', [CountryController::class, 'put']);
    Route::delete('/country/{id}', [CountryController::class, 'delete']);
```

### 2.5 Como probar tus endpoints

podes usar postman o el comando curl en tu terminal

Si el server es un apache, el endpoint del ejemplo anterior seria:

http://localhost:9090/mediacion-local/public/api/country

con el comando php artisan server, el endpoint seria:

http://localhost:8000/api/mediador


```bash
    curl --location 'http://localhost:9090/mediacion-local/public/api/mediador'
```

## 3. Acceso repositorio PJ

Es necesario crear una clave ssh
y para acceso se debe crear un archivo config dentro de la carpeta .ssh

en ese archivo meter estos cambios:

```notepad
    Host gitlab.local.jussantiago.gov.ar
    Port 2222
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa
```
