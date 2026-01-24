# 📖 Guía Completa: Instalación y Ejecución de GoFly desde Cero

¡Bienvenido! Esta guía te ayudará a ejecutar la aplicación GoFly en tu computadora sin necesidad de experiencia previa en programación.

---

## 📋 ¿Qué necesitas?

- Una computadora con Windows, Mac o Linux
- Conexión a internet
- ~10 GB de espacio en disco duro
- Paciencia ☺️

---

## **PASO 1: Instalar Git** 🔧

Git es una herramienta que te permite descargar el código del proyecto.

### Para Windows:
1. Abre tu navegador y ve a: https://git-scm.com/download/win
2. Haz clic en el botón verde **"Download"**
3. Espera a que se descargue el archivo (llamado `Git-X.XX.X-64-bit.exe`)
4. Abre el archivo descargado haciendo doble clic
5. Sigue el instalador (puedes hacer clic en "Next" en todas las ventanas)
6. Al final, haz clic en "Finish"

### Para Mac:
1. Abre la terminal (presiona `Cmd + Espacio` y escribe "Terminal")
2. Copia y pega esto en la terminal:
   ```
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   brew install git
   ```
3. Presiona Enter y espera a que termine

### Verificar que está instalado:
1. Abre "Símbolo del sistema" (Windows) o Terminal (Mac/Linux)
2. Escribe: `git --version`
3. Presiona Enter
4. Deberías ver un número de versión (ej: `git version 2.40.0`)

---

## **PASO 2: Descargar el Repositorio** 📥

Ahora vamos a descargar el código del proyecto GoFly.

### Para Windows:
1. Abre el Símbolo del sistema:
   - Presiona `Windows + R`
   - Escribe `cmd`
   - Presiona Enter

2. Copia y pega este comando y presiona Enter:
   ```
   git clone https://github.com/JulioChaverra/GoFly.git
   ```
   
3. Espera a que termine (verás mensajes en la pantalla)

4. Cuando termine, escribe:
   ```
   cd GoFly
   ```
   Presiona Enter

### Para Mac/Linux:
1. Abre la Terminal
2. Copia y pega:
   ```
   git clone https://github.com/JulioChaverra/GoFly.git
   cd GoFly
   ```
3. Presiona Enter

✅ **¡Listo!** Ahora tienes el código en tu computadora.

---

## **PASO 3: Instalar Docker** 🐳

Docker es un programa que crea "contenedores" (como máquinas virtuales pequeñas) para ejecutar la aplicación sin conflictos.

### Para Windows:

1. Ve a: https://www.docker.com/products/docker-desktop
2. Haz clic en **"Download for Windows"**
3. Espera a que se descargue `Docker Desktop Installer.exe`
4. Abre el archivo descargado (doble clic)
5. En la ventana que aparece, déjalo todo como está y haz clic en **"Install"**
6. Espera a que termine (puede tardar varios minutos)
7. Reinicia tu computadora cuando se lo pida

### Para Mac:

1. Ve a: https://www.docker.com/products/docker-desktop
2. Descarga la versión para tu Mac (Intel o Apple Silicon)
3. Abre el archivo descargado
4. Arrastra el icono de Docker a la carpeta "Applications"
5. Espera a que se copie
6. Abre Aplicaciones > Docker
7. Sigue las instrucciones que aparecen

### Para Linux:

Abre la Terminal y ejecuta:
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

### Verificar que Docker está instalado:

1. Abre el Símbolo del sistema o Terminal
2. Escribe:
   ```
   docker --version
   ```
3. Presiona Enter
4. Deberías ver algo como: `Docker version 24.0.0, build 12345`

**Nota importante:** Después de instalar Docker, espera 2-3 minutos antes de continuar para que inicie correctamente.

---

## **PASO 4: Ejecutar la Aplicación** ▶️

Ahora viene lo emocionante: ¡vamos a ejecutar GoFly!

### Para Windows:

1. **Abre el Símbolo del sistema** (Windows + R, escribe `cmd`, Enter)

2. **Ve a la carpeta del proyecto:**
   ```
   cd GoFly
   ```
   Presiona Enter

3. **Inicia la aplicación:**
   ```
   docker compose up --build
   ```
   Presiona Enter

4. **Espera** a que termine (puede tardar 5-10 minutos la primera vez)

5. Cuando veas mensajes como:
   ```
   flight-frontend | Node Express server listening on http://localhost:4200
   gateway          | Started gateway
   ```
   ¡La aplicación está lista!

### Para Mac/Linux:

1. Abre la Terminal
2. Ve al proyecto:
   ```
   cd GoFly
   ```
3. Inicia:
   ```
   docker compose up --build
   ```
4. Espera a que termine

---

## **PASO 5: Acceder a la Aplicación** 🌐

Una vez que Docker está corriendo, abre tu navegador (Chrome, Firefox, Safari, Edge) y ve a:

```
http://localhost:4200
```

¡Deberías ver la aplicación GoFly cargada! 🎉

---

## **¿Qué voy a ver?**

La aplicación tiene estos componentes ejecutándose:

- **Frontend (Angular)**: La interfaz visual (puerto 4200) ← Aquí haces clic
- **Gateway (API)**: El servidor que recibe tus solicitudes (puerto 8080)
- **Flight Prediction**: El servicio que predice vuelos (puerto 8090)
- **Eureka**: El sistema que gestiona los servicios (puerto 8761)
- **Config Server**: El servidor de configuración (puerto 8888)
- **MySQL**: La base de datos (puerto 3306)
- **ML Service**: El servicio de inteligencia artificial (puerto 8000)

---

## **Detener la Aplicación** ⏹️

Cuando termines de usar GoFly:

1. En el Símbolo del sistema/Terminal donde está corriendo Docker
2. Presiona `Ctrl + C` (mantén Ctrl presionado y presiona C)
3. Escribe:
   ```
   docker compose down
   ```
4. Presiona Enter

---

## **Problemas Comunes** 🆘

### ❌ Error: "docker: command not found"
**Solución:** Docker no está instalado. Vuelve al PASO 3 y asegúrate de instalarlo correctamente. Después reinicia la Terminal.

### ❌ Error: "Port 3306 already in use"
**Solución:** Tienes instalado MySQL y esta corriendo en tu computadora. para solucionarlo:

#### **Detener el proceso MySQL que está usando el puerto**

⚠️ **IMPORTANTE:** Estos comandos deben ejecutarse en una **Terminal o Símbolo del sistema ejecutado como ADMINISTRADOR**.

**Para Windows (como Administrador):**

1. Abre el Símbolo del sistema como Administrador:
   - Presiona `Windows + X`
   - Selecciona **"Terminal (administrador)"** o **"Símbolo del sistema (administrador)"**
   - Haz clic en **"Sí"** cuando te pida confirmación

2. Busca qué proceso está usando el puerto 3306:
   ```
   netstat -ano | findstr :3306
   ```
   
3. Verás una línea como:
   ```
   TCP    0.0.0.0:3306    0.0.0.0:0    LISTENING    1234
   ```
   El número al final (ej: `1234`) es el ID del proceso

4. Detén ese proceso con:
   ```
   taskkill /PID 1234 /F
   ```
   (Reemplaza `1234` con el número que viste)

**Para Mac/Linux (como sudo):**

1. Abre la Terminal

2. Busca qué proceso está usando el puerto 3306:
   ```
   sudo lsof -i :3306
   ```

3. Verás algo como:
   ```
   mysqld    12345    user    20u    IPv4    0x1234    0t0    TCP    localhost:3306
   ```
   El número `12345` es el ID del proceso

4. Detén ese proceso con:
   ```
   sudo kill -9 12345
   ```
   (Reemplaza `12345` con el número que viste)

### ❌ Error: "Cannot connect to Docker daemon"
**Solución:** Docker no está ejecutándose. Abre Docker Desktop (Windows/Mac) o reinicia el servicio Docker (Linux).

### ❌ Página en blanco en localhost:4200
**Solución:** Espera 2-3 minutos más. Los servicios pueden tardar en iniciar. Recarga la página (F5) después.

### ❌ La aplicación es muy lenta
**Solución:** Docker necesita recursos. Cierra otros programas pesados (Chrome con muchas pestañas, Photoshop, etc.).

---

## **Comandos Útiles** 📝

Si quieres ver qué está pasando:

```bash
# Ver los logs (mensajes) de todos los contenedores
docker compose logs

# Ver logs de un servicio específico (ej: frontend)
docker compose logs frontend

# Ver los contenedores en ejecución
docker compose ps

# Reiniciar sin reconstruir
docker compose restart

# Limpiar todo (cuidado, borra datos)
docker compose down -v
```

---

## **Próximos Pasos** 🚀

- Explora la aplicación GoFly
- Si eres desarrollador y quieres modificar código, consulta el `README.md` principal

---

## **¿Necesitas Ayuda?** 💬

- Abre un issue en GitHub: https://github.com/JulioChaverra/GoFly/issues
- Revisa los archivos de documentación incluidos

---

**¡Gracias por usar GoFly! 🎉**
