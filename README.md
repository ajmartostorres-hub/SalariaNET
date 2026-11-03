<p align="center">
  <img src="assets/banner-salarianet.png"
       alt="SalariaNet - Simulador de redes informáticas"
       width="100%">
</p>

<p align="center">
  <strong>Simulador de redes informáticas para el aprendizaje</strong>
</p>

**SalariaNet** es un simulador de redes informáticas desarrollado en Python y PySide6, diseñado para facilitar el aprendizaje de redes en el aula.

Permite crear topologías de red, conectar dispositivos, configurar routers y switches, asignar direcciones IP y observar cómo se comunican los equipos. Todo ello mediante una interfaz gráfica en español y un entorno pensado para experimentar y aprender.

Disponible para **Windows y Linux**.

---

## ¿Qué puedes hacer con SalariaNet?

SalariaNet reúne en una misma aplicación las herramientas necesarias para diseñar, configurar y comprender el funcionamiento de una red informática.

### Diseña tu propia red

- Crea redes con ordenadores, portátiles, servidores, impresoras y dispositivos móviles.
- Incorpora routers, switches, hubs y puntos de acceso.
- Conecta dispositivos mediante cable o WiFi.
- Organiza la topología libremente sobre el área de trabajo.
- Añade anotaciones para documentar tus diseños.

### Configura los dispositivos

- Asigna direcciones IP de forma manual o mediante DHCP.
- Configura máscaras de subred, puertas de enlace y servidores DNS.
- Administra routers y switches mediante una terminal de comandos.
- Configura VLAN y enlaces troncales 802.1Q.
- Establece rutas estáticas entre redes.
- Comprueba las tablas ARP, MAC y las tablas de enrutamiento.

### Observa cómo funciona la red

- Ejecuta simulaciones paso a paso.
- Visualiza el recorrido de los paquetes.
- Consulta los eventos y protocolos que intervienen en la comunicación.
- Comprueba el resultado de las conexiones.
- Analiza los detalles de las diferentes capas de comunicación.

---

## Tres formas de trabajar

SalariaNet ofrece tres modos de funcionamiento que permiten trabajar desde los conceptos básicos de redes hasta situaciones prácticas en una red real.

### 01. Modo Simulado

<sub>Aprendizaje y experimentación</sub>

Toda la red funciona dentro del simulador. Los dispositivos, las direcciones IP y las comunicaciones se gestionan en el propio entorno de SalariaNet.

Es ideal para diseñar topologías, realizar prácticas y comprender cómo funcionan los protocolos de red sin necesidad de disponer de equipos físicos.

### 02. Modo Real

<sub>Conexión con el ordenador físico</sub>

Permite que uno de los ordenadores del esquema represente al equipo real en el que se está ejecutando SalariaNet.

El dispositivo utiliza la configuración de red del ordenador y permite ejecutar comandos reales como `ping`, `tracert`, `nslookup` o `arp`.

Así es posible relacionar el esquema diseñado con el funcionamiento de una red física.

### 03. Intranet del aula

<sub>Conecta los equipos de los alumnos</sub>

Permite conectar diferentes instalaciones de SalariaNet a través de la red local del centro educativo.

El profesor puede preparar una topología y los alumnos conectar sus propios equipos a ella.

De esta manera, varios ordenadores pueden participar en una misma práctica y observar cómo se comunican a través de la red del aula.

---

## Herramientas integradas

### Calculadora IP

Una herramienta para comprender y calcular los parámetros fundamentales de una red:

- Dirección de red.
- Dirección de broadcast.
- Primera y última dirección IP disponible.
- Número de direcciones para equipos.
- Representación binaria de la máscara.
- Desarrollo de los cálculos.

Incluye una memoria justificativa en PDF, especialmente pensada para trabajar el direccionamiento IP en ESO.

También dispone de una versión independiente que funciona desde el navegador.

### Calculadora y asignación automática de IP

Permite distribuir automáticamente las direcciones IP de los dispositivos de una topología, utilizando direccionamiento estático o DHCP y teniendo en cuenta las rutas entre routers.

Además, comprueba posibles errores de configuración en las direcciones IP.

### Terminal de comandos

Incluye una interfaz de comandos inspirada en Cisco IOS, con abreviaturas, ayuda contextual y diferentes modos de configuración.

Permite trabajar con:

- Interfaces de red.
- VLAN y puertos troncales.
- DHCP.
- Rutas estáticas.
- Tablas de enrutamiento.
- Tablas ARP y MAC.
- Spanning Tree simplificado.

### Impresión y documentación

Los esquemas y sus configuraciones pueden exportarse a PDF para documentar y entregar las prácticas realizadas.

---

## Descargar SalariaNet

Puedes descargar las versiones preparadas para utilizar directamente desde GitHub.

**[DESCARGAR SALARIANET — VERSIONES DISPONIBLES](https://github.com/ajmartostorres-hub/SalariaNET/releases)**

### Windows 10 y 11

1. Descarga el archivo `SalariaNet.zip`.
2. Descomprime su contenido.
3. Ejecuta `SalariaNet.exe`.

No necesitas instalar Python ni configurar dependencias adicionales.

### Ubuntu 20.04 o posterior (64 bits)

1. Descarga el paquete `.deb` correspondiente.
2. Abre un terminal en la carpeta de descarga.
3. Ejecuta:

```bash
sudo apt install ./salarianet_*_amd64.deb
```

4. Inicia SalariaNet desde el menú de aplicaciones o ejecutando:

```bash
salarianet
```

Para desinstalar:

```bash
sudo apt remove salarianet
```

---

## Documentación

Para profundizar en el funcionamiento de la aplicación tienes disponibles los siguientes recursos:

- **Guía de usuario:** `docs/Guia_SalariaNet_actualizada.pdf`
- **Memoria de la calculadora IP:** `docs/Memoria_calculadora_IP.pdf`
- **Calculadora IP online:** `web/calculadora_ip.html`

También puedes consultar la ayuda integrada en el programa.

---

## Tecnologías utilizadas

SalariaNet está desarrollado utilizando:

| Tecnología | Utilización |
|---|---|
| Python | Lenguaje de programación |
| PySide6 / Qt 6 | Interfaz gráfica |
| PyInstaller | Distribución para Windows |
| Debian packages | Distribución para Ubuntu |

---

## Funcionalidades en desarrollo

SalariaNet es un proyecto en evolución. Entre las funcionalidades que todavía no están implementadas se encuentran:

- Enrutamiento dinámico (RIP y OSPF).
- NAT.
- Listas de control de acceso (ACL).
- Router-on-a-stick y subinterfaces.
- Servicios Telnet y SSH.
- Servicios de correo y FTP.
- Configuración de tipos de cable.
- Vista física de la infraestructura de red.

---

## Código fuente

SalariaNet es un proyecto desarrollado en Python y organizado en diferentes módulos para facilitar su mantenimiento y ampliación.

Si quieres consultar el código, colaborar o ejecutar el proyecto desde su código fuente, puedes utilizar este repositorio.

**[Consultar el código fuente en GitHub](https://github.com/ajmartostorres-hub/SalariaNET)**

### Ejecución desde el código fuente

Requisitos: Python 3.8 o posterior.

```bash
python -m venv .venv
```

En Windows:

```bash
.venv\Scripts\activate
```

En Linux:

```bash
source .venv/bin/activate
```

Instala las dependencias:

```bash
pip install -r requirements.txt
```

Ejecuta la aplicación:

```bash
python red_aula.py
```

---

## Licencia

SalariaNet es software libre y se distribuye bajo los términos de la **GNU General Public License v3.0 o posterior (GPL-3.0-or-later)**.

Consulta el archivo `LICENSE` para conocer las condiciones de uso, modificación y distribución.

---

**SalariaNet © 2026**

*Una herramienta para aprender redes, experimentar con ellas y comprender cómo funciona Internet desde el aula.*
