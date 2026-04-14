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

🌐 **Sitio oficial de descarga:**  
https://www.wampserver.com/en/download-wampserver-64bits/


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
composer

Si la instalación fue exitosa, se mostrará la información de Composer en pantalla.

<p align="center"> <img src="https://github.com/user-attachments/assets/f3c8b25d-70a1-4632-a2a1-26eae2e23ba5" width="700"> </p>

---

### 🔹 Paso 3: Configurar entorno

```bash id="pgklcy"
cp .env.example .env
php artisan key:generate
```

---

### 🔹 Paso 4: Configurar base de datos

Editar el archivo `.env`:

```env id="3xw4q6"
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel_login
DB_USERNAME=root
DB_PASSWORD=
```

---

### 🔹 Paso 5: Ejecutar migraciones

```bash id="yt0sfe"
php artisan migrate
```

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
