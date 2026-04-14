# 🧪 Laboratorio #2 - Implementación del Login en Laravel


## 📚 UNIVERSIDAD TECNOLÓGICA DE PANAMÁ

**Facultad de Ingeniería de Sistemas Computacionales**
Campus Víctor Levi Sasso

**Curso:** Desarrollo de Software VII
**Instructor:** Ing. Irina Fong

---


## 📖 Introducción

El presente laboratorio tiene como propósito documentar la implementación de un sistema de autenticación (Login) utilizando el framework Laravel, aplicando el patrón de arquitectura **Modelo-Vista-Controlador (MVC)**.

Este patrón permite organizar la aplicación en tres componentes principales: modelos, vistas y controladores, facilitando la separación de responsabilidades, el mantenimiento del sistema y su escalabilidad.

Durante el desarrollo se implementaron funcionalidades como:

* Registro de usuarios
* Inicio de sesión
* Cierre de sesión
* Validación de formularios

---

## 🎯 Objetivos de la Tarea

* Comprender la importancia de la documentación
* Aplicar la arquitectura MVC en Laravel
* Implementar un sistema de autenticación funcional
* Configurar correctamente el entorno
* Resolver problemas durante el desarrollo

---

## ⚙️ Requisitos Previos

|  Tecnología        |    Versión Requerida |    Descripción                      |
| ------------------ | -------------------- | ----------------------------------- |
| PHP                | 8.0 o superior       | Lenguaje de programación principal  |
| Laravel            | 10.x                 | Framework de desarrollo web         |
| Composer           | Última versión       | Gestor de dependencias de PHP       |
| MySQL              | 8.0 o superior       | Sistema de gestión de base de datos |
| Apache             | 2.4 o superior       | Servidor web                        |
| Node.js            | Opcional             | Compilación de assets               |
| NPM                | Opcional             | Gestión de paquetes                 |
| Visual Studio Code | Recomendado          | Editor de código                    |
| Git                | Última versión       | Control de versiones                |

---

## 🖥️ Entorno de Desarrollo

|   Componente     |   Detalle         |
| ----------------- | ------------------ |
| Sistema Operativo | Windows 10/11      |
| Servidor Local    | WampServer         |
| Base de Datos     | MySQL              |
| Editor de Código  | Visual Studio Code |

---

## 🚀 Instalación y Configuración
### 🔹 Paso 1: Instalación y verificación de WampServer

Para ejecutar el proyecto, es necesario contar con un servidor local. En este caso, se utilizó WampServer.

#### 📥 Descarga de WampServer

A continuación, se muestra la página oficial de descarga:

<p align="center">
  <img src="https://github.com/user-attachments/assets/29cf94df-eb6e-4b61-8c62-1aadcb58d6c3" width="700">
</p>


#### ✅ Verificación del estado del servidor

Después de la instalación, es importante verificar que WampServer esté en funcionamiento.  
El ícono debe mostrarse en color **verde**, lo que indica que todos los servicios (Apache y MySQL) están activos correctamente.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a551cb29-1c0c-4e1e-bfd2-d72fd7c290bb" width="300">
</p>



📌 **Nota:**  
Si el ícono no está en verde, significa que algún servicio no está iniciado y Laravel no funcionará correctamente.

---

### 🔹 Paso 2: Instalación de Composer

Composer es una herramienta necesaria para gestionar las dependencias de Laravel.


#### 📥 Descarga e instalación

Para instalar Composer, se debe ejecutar el archivo **Composer-Setup.exe** descargado previamente.

<p align="center">
  <img src="https://github.com/user-attachments/assets/85e520c3-d005-4d70-86ee-29d32086367a" width="700">
</p>


#### ✅ Verificación de instalación

Una vez finalizada la instalación, se debe verificar que Composer funcione correctamente.

Para ello, abrir la consola (CMD) y ejecutar el siguiente comando:
```bash
composer
```
Si la instalación fue exitosa, se mostrará la información de Composer en pantalla.

<p align="center"> <img src="https://github.com/user-attachments/assets/f3c8b25d-70a1-4632-a2a1-26eae2e23ba5" width="700"> </p>

---

### 🔹 Paso 3: Instalación de Laravel

En este paso se realiza la creación del proyecto Laravel dentro del directorio del servidor local (WampServer).



#### 💻 Ejecución de comandos

Se abre la consola (CMD) y se navega hasta la carpeta `www` donde se almacenan los proyectos:

```bash
C:\Windows\System32>cd..
C:\Windows>cd..
C:\>cd wamp64
C:\wamp64>cd www
C:\wamp64\www>laravel new labLaravelLogin7
```
📸 Resultado en consola
<p align="center"> <img src="https://github.com/user-attachments/assets/f958da34-bfa7-46c9-b8d3-2ac473f16a3c" width="800"> </p>

---

### 🔹 Paso 4: Abrir el proyecto en Visual Studio Code y configurar la base de datos

En este paso se abre la carpeta del proyecto Laravel en Visual Studio Code para realizar la configuración de la base de datos.


#### 📂 Apertura del proyecto

Se debe abrir la carpeta creada (`labLaravelLogin7`) en Visual Studio Code.

<p align="center">
  <img src="https://github.com/user-attachments/assets/437faf96-b788-49bc-a69b-9a7fc40b7279" width="800">
</p>



#### ⚙️ Configuración del archivo `.env`

Luego, se procede a editar el archivo `.env` para establecer la conexión con la base de datos MySQL:

```env id="j7k2hp"
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel_login
DB_USERNAME=root
DB_PASSWORD=
```

📌 **Nota:**  
Es importante asegurarse de que la base de datos laravel_login exista en MySQL antes de ejecutar las migraciones.

---

### 🔹 Paso 5: Ejecución de comandos y configuración del sistema

En este paso se ejecutan comandos en la terminal de Visual Studio Code y se realiza una configuración adicional en el proyecto Laravel.

#### 💻 Ejecución de comandos en la terminal

Abrir la terminal en Visual Studio Code y ejecutar los siguientes comandos:

```bash
php artisan config:clear
php artisan config:cache
```
Estos comandos permiten limpiar y actualizar la configuración del sistema.

<p align="center"> <img src="https://github.com/user-attachments/assets/f88b0084-cd18-424d-af89-18a86d700db1" width="800"> </p>

####⚙️ Configuración del archivo AppServiceProvider

Se debe realizar un ajuste en el archivo:

📁 app/Providers/AppServiceProvider.php

Agregar la siguiente configuración dentro del método boot():

```<?php

namespace App\Providers;

use Illuminate\Support\ServiceProvider;
use Illuminate\Support\Facades\Schema;
class AppServiceProvider extends ServiceProvider
{
    /**
     * Register any application services.
     */
    public function register(): void
    {
        //
    }

    /**
     * Bootstrap any application services.
     */
    public function boot(): void
    {
        Schema::defaultStringLength(191);
    }
}
```

<img width="1919" height="844" alt="image" src="https://github.com/user-attachments/assets/f46e01df-41f5-4349-866b-c50f22b9abc1" />


---

### 🔹 Paso 6: Ejecución de Migraciones

En este paso se crean las tablas necesarias en la base de datos mediante las migraciones de Laravel.


#### 💻 Ejecutar comando

Abrir la terminal en Visual Studio Code y ejecutar el siguiente comando:

```bash
php artisan migrate
```

Al ejecutar el comando, el sistema solicitará confirmación.
Se debe escribir yes para continuar con el proceso.

📸 Resultado de la ejecución
<p align="center"> <img src="https://github.com/user-attachments/assets/3e3a8c5b-5a13-40f5-a658-3709a575919f" width="800"> </p>
---

### 🔹 Paso 7: Ejecución del servidor y verificación del sistema

En este paso se levanta el servidor de Laravel y se verifica el funcionamiento del proyecto.  
Además, se muestra la creación de la base de datos en phpMyAdmin.



#### 💻 Ejecutar servidor de Laravel

En la terminal de Visual Studio Code ejecutar:

```bash
php artisan serve
```
Este comando iniciará el servidor local y generará una URL como:

http://127.0.0.1:8000
<p align="center"> <img src="https://github.com/user-attachments/assets/c7d3adcd-312e-45fb-916e-bf0e16b940da" width="700"> </p>
🌐 Visualización en el navegador

Presionar Ctrl + Click sobre el enlace generado para abrir el proyecto en el navegador.

Si todo está correcto, se mostrará la página principal de Laravel.

<p align="center"> <img src="https://github.com/user-attachments/assets/24f6aff1-6c7f-4123-b92a-e191ecf5286e" width="800"> </p>
🗄️ Creación de la base de datos en phpMyAdmin

Luego, se debe acceder a phpMyAdmin desde WampServer para crear la base de datos utilizada en el proyecto.

Se crea la base de datos con el nombre:

laravel_login
<p align="center"> <img src="https://github.com/user-attachments/assets/975cac60-1bb9-4cd7-9e97-3e90666ac861" width="800"> </p>

---
### 🔹 Paso 8: Bootstrap con login/registro
 Para entrar al Bootstrap con login/registro
---
## 🔐 Instalación del Sistema de Autenticación

Se utilizó Laravel UI con Bootstrap:

```bash id="h0y78o"
composer require laravel/ui
php artisan ui bootstrap --auth
npm install
npm run dev
```

---

## 🧱 Arquitectura MVC

### 📁 Modelos

* `User.php` → Representa la entidad usuario

---

### 🎮 Controladores

* `LoginController` → Maneja el login
* `RegisterController` → Registro de usuarios
* `HomeController` → Acceso protegido

---

### 🖼️ Vistas

* `auth/login.blade.php`
* `auth/register.blade.php`
* `home.blade.php`
* `layouts/app.blade.php`

---

### 🌐 Rutas

* Rutas públicas: login y register
* Rutas protegidas con middleware `auth`

---

## 🗄️ Base de Datos

### ⚙️ Configuración

* Motor: MySQL
* Nombre: laravel_login
* Codificación: UTF-8

---

### 🔧 Comandos utilizados

```bash id="z1kbhv"
php artisan migrate
php artisan migrate:status
php artisan migrate:rollback
```

---

### 📊 Tablas generadas

* users
* password_resets
* failed_jobs

---

## 📸 Resultados del Sistema

### 🔐 Pantalla de Login

📍 (XXXXXX - INSERTAR IMAGEN LOGIN AQUÍ)

---

### 📝 Pantalla de Registro

📍 (XXXXXX - INSERTAR IMAGEN REGISTER AQUÍ)

---

## ⚠️ Dificultades y Soluciones

---

### ❌ Problema 1: Node.js no instalado

**Dificultad:**
No se podían ejecutar los comandos de compilación.

**Solución:**

```bash id="5jc1gd"
npm install
npm run dev
```

---

### ❌ Problema 2: Versión de PHP incompatible

**Dificultad:**
PHP 8.5.0 generaba errores.

**Solución:**
Cambiar a PHP 8.1 o 8.2 en WampServer.

---

### ❌ Problema 3: Base de datos no creada

**Dificultad:**
Error al ejecutar migraciones.

**Solución:**

```bash id="df6xp4"
php artisan migrate
```

---

### ❌ Problema 4: Error en archivo .env

**Dificultad:**
Datos incorrectos de conexión.

**Solución:**
Corregir configuración en `.env`.

---

## 📚 Referencias

* https://laravel.com/docs
* https://getbootstrap.com/docs
* https://laracasts.com
* https://getcomposer.org/download/
* https://laravel.com/docs/12.x/installation
* https://www.wampserver.com/en/download-wampserver-64bits/

---

## 📅 Fecha de Ejecución

**8 de abril del 2026**

---

## 📦 Backup de Base de Datos

```id="t23u1j"
/database/backups/database_backup.sql
```

---

## 👨‍💻 Información del Estudiante

* **Nombre:** Ana Cheung
* **Correo:** [ana.cheung1@utp.ac.pa](mailto:ana.cheung1@utp.ac.pa)
* **Curso:** Desarrollo de Software VII
* **Instructor:** Ing. Irina Fong

---

## 📅 Fecha de Entrega

**15 de abril del 2026**
