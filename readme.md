
# Contenido

1. Instalaciones recomendadas
2. Como empezar con Laravel
3. Acceso a repositorio del PJ

## 1. Instalaciones recomendadas

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

## 2. Crear empezar con laravel


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
