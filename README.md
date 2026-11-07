# Launcher Spark LTZ 2016

Launcher ligero para Chevrolet Spark LTZ 2016 Classic, hecho para la
pantalla china **A100, Android 13, 2 GB RAM, 64 GB**.

Es la misma idea del diseño de referencia: saludo con tu nombre,
hora y fecha en vivo en español, clima, música y 6 botones grandes
abajo: Maps, Waze, Spotify, Radio FM, Bluetooth y Aplicaciones.
La foto del auto es un Spark LTZ 2016 plata al atardecer
(`app/src/main/res/drawable/spark_ltz.webp`).

## Qué incluye

- `AndroidManifest.xml` — MainActivity como pantalla principal (HOME).
- `app/build.gradle` y `build.gradle` — targetSdk 33, minSdk 26,
  Kotlin, solo AppCompat, sin Compose y sin dependencias externas.
- `app/src/main/java/com/noe/sparklauncher/MainActivity.kt` — reloj
  en vivo, fecha en español, saludo según la hora, cajón de apps y
  apertura por paquete con regreso a Play Store si falta la app.
- `app/src/main/res/layout/activity_main.xml` — barra superior,
  barra lateral, clima, música y los 6 botones.
- `app/src/main/res/drawable/spark_ltz.webp` — foto del Spark.

## Apps que abre cada botón

| Botón | Paquete que busca |
| --- | --- |
| Maps | `com.google.android.apps.maps` |
| Waze | `com.waze` |
| Spotify | `com.spotify.music` |
| Radio FM | radio del sistema (prueba varios paquetes comunes) |
| Bluetooth | Ajustes de Bluetooth del sistema |
| Aplicaciones | lista de todas las apps instaladas |

Si una app no está instalada, abre su página en Play Store.
El clima es un texto editable en el diseño (`28°C, Parcialmente
nublado`): no usa clave de API ni internet. Para cambiarlo, edita
ese texto en `activity_main.xml`.

## Cómo compilar el APK (en una PC)

1. Instala **Android Studio** (versión reciente) en la PC.
2. Copia esta carpeta `android/` a la PC y ábrela en Android Studio
   como proyecto. Espera a que descargue Gradle y el SDK.
3. Conecta la pantalla A100 por USB o solo compila el APK:
   **Build > Build App Bundle(s) / APK(s) > Build APK(s)**.
4. Cuando termine, pulsa **locate** y copia el archivo
   `app-debug.apk` a una memoria USB.

Si quieres un APK firmado para instalarlo siempre igual, usa
**Build > Generate Signed Bundle / APK > APK**, crea una llave
nueva, guárdala bien, y compila en modo `release`.

## Cómo instalarlo en la pantalla A100

1. En la pantalla, ve a **Ajustes > Seguridad** (o **Ajustes >
   Apps > Acceso especial**) y activa **Instalar apps desconocidas**
   para el explorador de archivos o el instalador que uses.
   En algunas pantallas chinas está en **Ajustes > Seguridad >
   Fuentes desconocidas**.
2. Copia el APK a la pantalla con una memoria USB o por Wi-Fi.
3. Abre el APK con el explorador de archivos y pulsa **Instalar**.
4. Cuando Android pregunte qué launcher usar, elige
   **Launcher Spark LTZ** y pulsa **Siempre**.
   Si no pregunta, ve a **Ajustes > Apps > Apps predeterminadas >
   App de inicio** y elige **Launcher Spark LTZ**.
5. Si te pide permisos, acepta los que necesite para abrir apps.
   No necesita tu ubicación ni tus contactos para funcionar.
6. Para que no se cierre solo, ve a **Ajustes > Batería >
   Optimización de batería**, busca **Launcher Spark LTZ** y elige
   **No optimizar** o **Sin restricciones**. En algunas pantallas
   está en **Ajustes > Apps > Launcher Spark LTZ > Batería**.

## Para volver al launcher anterior

Ve a **Ajustes > Apps > Apps predeterminadas > App de inicio** y
elige el launcher original de la pantalla. También puedes
desinstalar este launcher desde **Ajustes > Apps**.

## Notas

- El launcher está fijo en horizontal, pensado para pantalla de auto.
- No usa animaciones pesadas para que vaya fluido con 2 GB de RAM.
- No se inventó una resolución exacta de pantalla: el diseño se
  adapta al tamaño de la A100 con pesos (`layout_weight`).
- La música en el prototipo es solo play/pausa de demostración;
  en el launcher real abre Spotify o tu app de música con los
  botones de abajo.
