# 🛠️ REVIQO

<p align="center">
  <b>Aplicación móvil moderna para la gestión integral de clientes, equipos y mantenimientos periódicos.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-green.svg" alt="Platform Android">
  <img src="https://img.shields.io/badge/Kotlin-Jetpack%2520Compose-purple.svg" alt="Jetpack Compose">
  <img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License Apache 2.0">
  <img src="https://img.shields.io/badge/Status-Active-orange.svg" alt="Status Active">
</p>

---

## 📱 ¿Qué es REVIQO?

**REVIQO** es una herramienta diseñada para profesionales y técnicos que necesitan llevar un control riguroso, rápido y organizado de sus clientes, los equipos que tienen bajo su responsabilidad y las tareas de mantenimiento preventivo ocorrectivo asociadas. 

Olvídate de las hojas de cálculo desordenadas; REVIQO centraliza todo en la palma de tu mano con una interfaz fluida y alertas automatizadas.

---

## ✨ Características Principales

* **👥 Gestión de Clientes:** Directorio completo con información de contacto y accesos directos (como integración con WhatsApp para avisos rápidos).
* **💻 Control de Equipos:** Registro detallado de equipos vinculados a cada cliente para un seguimiento exhaustivo de hardware o instalaciones.
* **🔧 Gestión de Mantenimientos:** Programación de citas y tareas, control de estados y supervisión de pendientes.
* **⏰ Alertas en Segundo plano:** Notificaciones automáticas impulsadas por `WorkManager` para que nunca se te pase un mantenimiento.
* **📂 Herramientas de Datos:**
  * Copias de seguridad locales y restauración sencilla.
  * Importación y exportación de datos mediante archivos CSV.
* **🗑️ Utilidades Avanzadas:** Papelera de reciclaje y opciones de privacidad configurables.

---

## 🛠️ Tecnologías y Arquitectura

El proyecto está desarrollado bajo los estándares actuales de desarrollo Android:
* **Lenguaje:** [Kotlin](https://kotlinlang.org/)
* **Interfaz de Usuario:** [Jetpack Compose](https://developer.android.com/jetpack/compose) con Material 3.
* **Persistencia de Datos:** [Room Database](https://developer.android.com/training/data-storage/room) (SQLite local).
* **Tareas en segundo plano:** [WorkManager](https://developer.android.com/topic/libraries/architecture/workmanager).
* **Arquitectura:** MVVM (Model-View-ViewModel) por capas orientada a características.
