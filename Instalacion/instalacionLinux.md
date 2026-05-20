<h1 align="center">Instalación del entorno Proxmark3 en Linux</h1>

<img width="1024" height="572" alt="image" src="https://github.com/user-attachments/assets/1c5557ff-3ad0-4ff0-92e4-02a6c495556f" />

---

## Índice
1. [Objetivo](#objetivo)
2. [Material necesario](#material-necesario)
3. [Procedimiento](#procedimiento)
4. [Resultados](#resultados)
5. [Conclusión](#conclusión)

---

## Objetivo

Instalar y compilar el cliente de Proxmark3 en un sistema Linux para preparar el entorno de trabajo utilizado durante el taller.

---

## Material necesario

- Ordenador con Linux
- Conexión a Internet
- Proxmark3

---

## Procedimiento

### Paso 1: Actualizar el sistema
---

Actualizar la lista de paquetes disponibles del sistema:

```bash
sudo apt update
```

<img width="1310" height="205" alt="Screenshot_1" src="https://github.com/user-attachments/assets/aa00919b-eb2c-4c1e-ba47-4df9818365b2" />

---
### Paso 2: Instalar dependencias necesarias
---

Instalar todas las dependencias necesarias para poder compilar el cliente de Proxmark3 en Linux:

```bash
sudo apt install --no-install-recommends git ca-certificates build-essential pkg-config \
libreadline-dev gcc-arm-none-eabi qtbase5-dev libbz2-dev liblz4-dev \
libbluetooth-dev libpython3-dev libssl-dev libgd-dev
```

<img width="1308" height="516" alt="Screenshot_2" src="https://github.com/user-attachments/assets/909ce2b1-f020-44ac-997f-e917c84f38a5" />

---
### Paso 3: Clonar el repositorio de Proxmark3
---

Descargar el repositorio oficial del cliente Proxmark3:

```bash
git clone https://github.com/RfidResearchGroup/proxmark3.git
```

<img width="1308" height="289" alt="Screenshot_3" src="https://github.com/user-attachments/assets/68274d2e-3a92-41e7-947a-1e698351e358" />

---
### Paso 4: Acceder al directorio del proyecto
---

Entrar en la carpeta descargada:

```bash
cd proxmark3
```

<img width="1309" height="303" alt="Screenshot_4" src="https://github.com/user-attachments/assets/7882e2fa-785d-46e8-b190-2d628bd897b1" />

---
### Paso 5: Seleccionar la versión utilizada en el taller
---

Cambiar al commit utilizado durante el taller para asegurar compatibilidad y estabilidad:

```bash
git checkout 3a5c0d81f
```

<img width="1307" height="489" alt="Screenshot_5" src="https://github.com/user-attachments/assets/e2b55683-1e15-4420-8297-ce1c49835b11" />

---
### Paso 6: Configurar la plataforma
---

Crear el archivo de configuración y seleccionar la plataforma genérica:

```bash
cp Makefile.platform.sample Makefile.platform

sed -i 's/^PLATFORM=PM3RDV4/# PLATFORM=PM3RDV4/' Makefile.platform

sed -i 's/# PLATFORM=PM3GENERIC/PLATFORM=PM3GENERIC/' Makefile.platform
```

<img width="1308" height="277" alt="Screenshot_6" src="https://github.com/user-attachments/assets/d5019203-238f-40b3-a057-b7f0d801c2b2" />

---
### Paso 7: Compilar el cliente Proxmark3
---

Compilar el cliente ejecutando el siguiente comando:

```bash
make clean && make client
```

<img width="1308" height="660" alt="Screenshot_7" src="https://github.com/user-attachments/assets/8d71b1e8-a251-40c4-9c9b-3156c419c45c" />

El proceso puede tardar varios minutos dependiendo del sistema.

<img width="1309" height="387" alt="Screenshot_8" src="https://github.com/user-attachments/assets/df27def7-2c25-4512-a30a-22388700e4f3" />

---
### Paso 8: Ejecutar el cliente
---

Una vez finalizada la compilación, ejecutar el cliente Proxmark3:

```bash
./pm3
```

<img width="1308" height="663" alt="Screenshot_9" src="https://github.com/user-attachments/assets/4941d083-e289-43b1-90e2-1f74a7d20dd3" />

Si la instalación se ha realizado correctamente, se abrirá la consola interactiva de Proxmark3.

---

## Resultados

El entorno de Proxmark3 queda correctamente instalado y compilado en el sistema Linux.

Se ha verificado que:
- Todas las dependencias necesarias se han instalado correctamente.
- El repositorio se ha clonado sin errores.
- La versión del proyecto corresponde al commit utilizado en el taller.
- La compilación del cliente finaliza de forma exitosa.
- El binario `pm3` se ejecuta correctamente y abre la consola interactiva.

Esto confirma que el sistema está listo para ser utilizado en las siguientes prácticas del taller de explotación RFID.

---

## Conclusión

La instalación del entorno en Linux permite disponer de una versión funcional del cliente Proxmark3 para interactuar con el dispositivo RFID.

Con este entorno preparado, se garantiza la compatibilidad con las herramientas utilizadas durante el taller, facilitando la ejecución de comandos de lectura, análisis y clonación de tarjetas RFID en las prácticas posteriores.
