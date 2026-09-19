<div align="center">

<img src="logo.png" alt="REVIQO" width="96">

# REVIQO

**No pierdas ningún mantenimiento.**

App Android *offline-first* para gestionar clientes, equipos y mantenimientos periódicos.
Sin servidores, sin cuentas y sin anuncios.

[![Versión](https://img.shields.io/badge/versión-1.0.0-1E3A5F)](https://github.com/lecodev-26/reviqo/releases/latest)
[![Android](https://img.shields.io/badge/Android-8.0%2B-3DDC84?logo=android&logoColor=white)](https://github.com/lecodev-26/reviqo/releases/latest)
[![Kotlin](https://img.shields.io/badge/Kotlin-2.0.20-7F52FF?logo=kotlin&logoColor=white)](https://kotlinlang.org/)
[![Compose](https://img.shields.io/badge/Jetpack%20Compose-Material%203-4285F4)](https://developer.android.com/jetpack/compose)

**[⬇ Descargar la APK](https://github.com/lecodev-26/reviqo/releases/download/v.1.0.0/reviqo.apk)** · **[🌐 Web](https://lecodev-26.github.io/reviqo/)** · **[📋 Notas de la versión](https://github.com/lecodev-26/reviqo/releases/tag/v.1.0.0)**

</div>

---

## ¿Qué problema resuelve?

El trabajo de mantenimiento tiene una trampa: lo importante no es lo que haces hoy, sino lo que toca dentro de seis meses. Una revisión que se pasa no avisa. Simplemente pasa la fecha, y la siguiente señal llega cuando algo se rompe.

Entre la hoja de cálculo que se desordena sola y el software de gestión de campo con cuota mensual no había nada intermedio. **REVIQO ocupa ese hueco**: abres la app y en dos segundos sabes qué está vencido, qué está cerca y qué está al día. Y si no la abres, te avisa ella.

### Para quién es

Técnicos y autónomos que gestionan sus propios clientes: climatización, extinción de incendios, refrigeración, informática con parque de equipos, talleres con revisiones periódicas. Gente que trabaja sola o en equipos muy pequeños y necesita consultar cosas de pie, con una mano y a veces sin cobertura.

### Para quién no

Si necesitas que varios técnicos compartan agenda en tiempo real, facturación integrada o partes firmados por el cliente, esta no es tu herramienta. La V1 no sincroniza entre dispositivos: los datos viven en un móvil, el tuyo.

---

## Características

| | Qué hace |
|---|---|
| 👥 **Clientes** | Directorio con contacto, dirección y notas. Llamada y aviso por WhatsApp con el mensaje redactado desde la propia ficha. |
| 💻 **Equipos** | Marca, modelo, número de serie, ubicación y fotos, siempre vinculados a un cliente. |
| 🔧 **Mantenimientos** | Programación periódica con recálculo automático de la siguiente fecha al marcarlo como hecho. Estados: vencido, próximo, al día. |
| ⏰ **Avisos automáticos** | Comprobación periódica con `WorkManager`. Funciona con la app cerrada y sobrevive a reinicios del teléfono. |
| 📂 **CSV** | Importación y exportación de clientes y equipos. Tus datos entran y salen sin quedarse atrapados. |
| 💾 **Copias de seguridad** | Backup local completo y restauración en un paso. |
| 🗑️ **Papelera** | Borrado suave con restauración o eliminación definitiva. |
| 🔒 **Privacidad** | Política incluida en la app y borrado total de datos desde Ajustes. |

---

## Privacidad y seguridad

REVIQO no tiene backend. No es una promesa comercial: no existe el sitio al que enviar los datos.

- Sin servidores, sin cuentas, sin registro
- Sin analítica, sin rastreadores y sin anuncios
- Base de datos en el almacenamiento interno **privado** de la app
- Las fotos se guardan fuera de la galería pública
- Solo **dos permisos**: notificaciones (`POST_NOTIFICATIONS`) y reanudar tareas tras reiniciar (`RECEIVE_BOOT_COMPLETED`)
- Exportaciones y copias solo cuando el usuario las inicia
- El envío por WhatsApp siempre lo confirma el usuario
- Opción de **borrar todos los datos** en Ajustes

> Como manejas datos de terceros, tú eres el responsable del tratamiento. La app está construida para ponértelo fácil.

---

## Instalación

La APK se instala manualmente, fuera de la tienda.

1. Descarga [`reviqo.apk`](https://github.com/lecodev-26/reviqo/releases/download/v.1.0.0/reviqo.apk) (117,5 MB) **desde el móvil**.
2. Abre el archivo desde la notificación de descarga o desde Archivos → Descargas.
3. Cuando Android avise de que no viene de la tienda, entra en Ajustes y permite la instalación desde esa fuente.
4. Al abrir REVIQO, concede el permiso de notificaciones.
5. En Ajustes de Android → Aplicaciones → REVIQO → Batería, elige **«Sin restricciones»** para que los avisos no se retrasen.

**Requisitos:** Android 8.0 (API 26) o superior.

```
SHA-256  42845698cbaa217241e3cd14dd3e1ebb3dd4dffaeb5a00cbc129cbeb3a13f1c3
```

---

## Stack técnico

| Capa | Tecnología |
|---|---|
| Lenguaje | [Kotlin](https://kotlinlang.org/) 2.0.20 |
| Interfaz | [Jetpack Compose](https://developer.android.com/jetpack/compose) + Material 3 |
| Persistencia | [Room](https://developer.android.com/training/data-storage/room) (SQLite local) |
| Segundo plano | [WorkManager](https://developer.android.com/topic/libraries/architecture/workmanager) |
| Arquitectura | MVVM por capas, orientada a características |
| Compilación | Gradle KTS · AGP 8.5.2 · KSP |

**Package:** `com.reviqo.app` · **minSdk** 26 · **targetSdk** 35 · **JDK** 17

### Estructura del proyecto

```
app/src/main/java/com/reviqo/app/
├── data/
│   ├── local/          # Room: base de datos y DAOs
│   ├── model/          # Cliente, Equipo, Mantenimiento
│   └── repository/     # Acceso a datos por entidad
├── ui/
│   ├── navigation/     # NavGraph
│   ├── screens/        # Home, clientes, equipos, mantenimientos, ajustes
│   ├── theme/          # Color, Type, Theme
│   └── viewmodel/      # Un ViewModel por área
├── util/               # CSV, backup, notificaciones, WhatsApp, imágenes
├── worker/             # MantenimientoCheckWorker
├── MainActivity.kt
└── REVIQOApp.kt
```

---

## Compilar desde el código

### Android Studio

1. Abre la carpeta del proyecto y espera a que sincronice Gradle.
2. **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
3. La APK queda en `app/build/outputs/apk/debug/app-debug.apk`.

### Línea de comandos

Necesitas JDK 17 o 21, el Android SDK (API 35 + build-tools 35) y `ANDROID_HOME` apuntando al SDK.

```bash
cp local.properties.example local.properties
# edita local.properties con tu sdk.dir

chmod +x gradlew
./gradlew assembleDebug        # APK de depuración
./gradlew assembleRelease      # APK de release (requiere firma)
```

> La primera compilación descarga dependencias y puede tardar varios minutos.

---

## Estado y roadmap

| Área | Estado |
|---|---|
| Clientes, equipos y mantenimientos | ✅ |
| Cálculo automático de fechas | ✅ |
| Lista de pendientes | ✅ |
| Notificaciones en segundo plano | ✅ |
| Aviso por WhatsApp | ✅ |
| Fotos de equipos | ✅ |
| Importar / exportar CSV | ✅ |
| Copia de seguridad y restauración | ✅ |
| Papelera con restauración | ✅ |
| Privacidad y borrado total | ✅ |
| Firma de release y publicación en tiendas | 🔜 |
| Sincronización opcional entre dispositivos | 🤔 Por decidir |

---

## Contribuir

Si la usas y algo te chirría, falta una función o encuentras un fallo, abre una [issue](https://github.com/lecodev-26/reviqo/issues). Es la forma más rápida de que acabe arreglado.

---

## Autor

**Manuel Echepares** — [@lecodev-26](https://github.com/lecodev-26)

<div align="center">
<sub>REVIQO 1.0.0 · 2026</sub>
</div>
