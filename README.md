# 🚀 Parcial 3 - Soluciones en .NET (C#)

<p align="center">
  <b>Universidad Tecnológica de Panamá (UTP)</b><br>
  Facultad de Ingeniería de Sistemas Computacionales<br>
  Desarrollo de Software
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Author-Neo-blue.svg?style=flat-square&logo=github" alt="Autor">
  <img src="https://img.shields.io/badge/Language-C%23-239120.svg?style=flat-square&logo=csharp" alt="C#">
  <img src="https://img.shields.io/badge/.NET-Windows%20Forms-512BD4.svg?style=flat-square&logo=dotnet" alt=".NET">
  <img src="https://img.shields.io/badge/Database-MySQL-4479A1.svg?style=flat-square&logo=mysql&logoColor=white" alt="MySQL">
</p>

---

## 📌 Descripción General
Este repositorio recopila los desarrollos prácticos correspondientes al **Parcial 3**, estructurados en tres módulos principales que abarcan desde los fundamentos de la Programación Orientada a Objetos y manejo de datos, hasta la implementación de un sistema de autenticación robusto y seguro.

---

## 🛠️ Tecnologías y Dependencias
* **Lenguaje:** C# (.NET)
* **Interfaz Gráfica:** Windows Forms
* **Base de Datos:** MySQL Server (`MySql.Data`)
* **Seguridad / Cifrado:** `BCrypt.Net-Next`
* **Serialización:** `Newtonsoft.Json`

---

## 📂 Estructura y Módulos del Proyecto

### 📐 1. Polimorfismo y Jerarquía de Clases (`Parcial3_Polimorfismo`)
* **Enfoque:** Aplicación de los principios de Programación Orientada a Objetos (POO).
* **Características:** Implementación de clases base, clases derivadas y sobrescritura de métodos (`override`) para el cálculo dinámico de áreas y perímetros en figuras geométricas.

### 📦 2. Manejo de Datos y Serialización JSON (`Parcial3_Json`)
* **Enfoque:** Persistencia ligera y estructuración de la información.
* **Características:** Uso de librerías especializadas para transformar objetos complejos en formato JSON y viceversa, facilitando el intercambio y almacenamiento de datos.

### 🔐 3. Sistema de Autenticación y Auditoría (`Parcial3_Login`)
* **Enfoque:** Seguridad de aplicaciones y conexión a bases de datos relacionales.
* **Características:**
  * **Hashing con BCrypt:** Las contraseñas se almacenan cifradas y se validan de forma segura mediante `BCrypt.Verify()`.
  * **Bitácora de Intentos:** Registro automatizado en tiempo real de los accesos (**Exitosos** y **Fallidos**), guardando el usuario, el estado y la fecha exacta.
  * **Interfaz Interactiva:** Validación visual y bienvenida personalizada indicando el nombre del usuario al iniciar sesión correctamente.

---

## 🗄️ Configuración de la Base de Datos (`Parcial3DB`)

Para la **Parte 3**, ejecuta el siguiente script SQL en tu gestor de MySQL Workbench para crear la estructura de tablas necesaria:

```sql
CREATE DATABASE IF NOT EXISTS Parcial3DB;
USE Parcial3DB;

-- Tabla de Usuarios
CREATE TABLE IF NOT EXISTS Usuarios (
    Id INT AUTO_INCREMENT PRIMARY KEY,
    Usuario VARCHAR(50) NOT NULL,
    PasswordHash VARCHAR(255) NOT NULL
);

-- Tabla de Auditoría (Intentos de Login)
CREATE TABLE IF NOT EXISTS IntentosLogin (
    Id INT AUTO_INCREMENT PRIMARY KEY,
    Usuario VARCHAR(50) NOT NULL,
    Estado VARCHAR(20) NOT NULL, -- 'Exitoso' o 'Fallido'
    Fecha DATETIME DEFAULT CURRENT_TIMESTAMP
);
