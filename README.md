<p align="center">
  <img src="recursos/logo.png" alt="Logotipo de SalariaNet" width="180">
</p>

<h1 align="center">SalariaNet</h1>

<p align="center">
  <b>Simulador de redes en español para el aula</b><br>
  Dibuja una red, configura los equipos y mira cómo viajan los paquetes.<br>
  Funciona en <b>Windows</b> y en <b>Linux</b>.
</p>

<p align="center">
  <a href="../../releases/latest"><img src="https://img.shields.io/badge/Descargar-%C3%BAltima%20versi%C3%B3n-2ea44f?style=for-the-badge&logo=github" alt="Descargar la última versión"></a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/licencia-GPLv3%2B-blue" alt="Licencia GPL v3 o posterior"></a>
  <img src="https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?logo=windows" alt="Windows 10 y 11">
  <img src="https://img.shields.io/badge/Ubuntu-20.04%2B-E95420?logo=ubuntu&logoColor=white" alt="Ubuntu 20.04 o posterior">
  <img src="https://img.shields.io/badge/Python-3.8%2B-3776AB?logo=python&logoColor=white" alt="Python 3.8 o posterior">
  <img src="https://img.shields.io/badge/Qt%206-PySide6-41CD52?logo=qt&logoColor=white" alt="PySide6 (Qt 6)">
</p>

![Un esquema de SalariaNet: dos redes unidas por un router, con un punto de acceso WiFi y un ping en curso](docs/capturas/esquema.png)

SalariaNet es un simulador de redes al estilo de Cisco Packet Tracer, pensado para las clases de redes:
todo en español, ligero y libre. Tiene tres formas de trabajar:

- **Simulado**: todo ocurre dentro del programa, con las IP del esquema.
- **Real**: un PC del esquema es el ordenador de verdad, con su IP y sus órdenes `ping`, `tracert`…
- **Intranet del aula**: los SalariaNet de varios ordenadores se unen y los paquetes viajan por la red del centro.

## Descargar e instalar

Las versiones listas para usar están en **[Releases](../../releases/latest)**
([todas las versiones](../../releases)).

### Windows 10 y 11

1. Descarga `SalariaNet.zip`.
2. Descomprímelo (clic derecho → *Extraer todo*).
3. Abre `SalariaNet.exe`. No hace falta instalar Python ni nada más.

La primera vez que uses el modo Real o la Conexión aula, Windows preguntará si SalariaNet puede usar la
red: hay que permitirlo en **redes privadas**.

### Ubuntu 20.04 o posterior (64 bits)

1. Descarga el archivo `salarianet_…_amd64.deb`.
2. En un terminal, desde la carpeta donde lo has descargado:

   ```bash
   sudo apt install ./salarianet_*_amd64.deb
   ```

   `apt` instala también las bibliotecas del sistema que falten (`dpkg -i` no lo hace).
3. Ábrelo desde el menú de aplicaciones o con la orden `salarianet`. Los esquemas `.red` se abren con
   doble clic.

El paquete ya lleva PySide6 (Qt 6), así que no hace falta `pip`. Si el centro tiene el cortafuegos
activado, hay que permitir SalariaNet una vez en cada ordenador:

```bash
sudo ufw allow SalariaNet
```

Para desinstalarlo: `sudo apt remove salarianet`.

### Desde el código fuente (cualquier sistema)

Hace falta Python 3.8 o posterior. Descarga el código (botón **Code → Download ZIP**).

- **Windows**: doble clic en `iniciar.bat`, que instala PySide6 la primera vez.
- **Linux**: en la carpeta del código, con un entorno virtual (en Ubuntu hace falta
  `sudo apt install python3-venv libxcb-cursor0`):

  ```bash
  python3 -m venv .venv
  . .venv/bin/activate
  pip install -r requirements.txt
  python red_aula.py
  ```

Para abrir un esquema guardado: `python red_aula.py esquema.red`. También abre los esquemas de la
versión 1.0.

## Capturas

| Simulación paso a paso | Terminal de un PC |
|---|---|
| ![Dos PDU simples: una correcta y otra en curso](docs/capturas/simulacion.png) | ![ping por nombre e ipconfig en el terminal de un PC](docs/capturas/terminal.png) |
| **Router con órdenes de Cisco IOS** | **Calculadora IP** |
| ![Configuración de un router con la CLI](docs/capturas/router_cli.png) | ![Calculadora IP con la IP en binario y las cuentas de cada resultado](docs/capturas/calculadora.png) |

## Qué incluye

| Packet Tracer | SalariaNet |
|---|---|
| PC, Laptop, Server, Printer | PC, Portátil, Servidor, Impresora |
| Smartphone, Tablet, TV | Móvil, Tablet, Smart TV |
| Hub, Switch 2960, Router, Access Point | Hub, Switch (24 Fa + 2 Gi), Router (4 Gi), Punto de acceso |
| Conexión con cable o inalámbrica | Cualquier equipo va por cable o por WiFi (al punto de acceso, dentro de su alcance) |
| Luces de enlace verde / rojo / ámbar | Igual (ámbar = puerto bloqueado por spanning tree) |
| Puertos del router apagados al principio | Igual: hay que hacer `no shutdown` o marcar «Encendida» |
| Desktop → IP Configuration (estática / DHCP) | Configuración IP con IP, máscara, puerta de enlace, DNS y DHCP |
| Desktop → Command Prompt | Terminal: `ipconfig [/all /renew /release]`, `ping`, `tracert`, `nslookup`, `arp`, `mensaje`, `imprimir` |
| Desktop → Web Browser | Navegador web (DNS + TCP + HTTP) |
| Server → Services HTTP / DNS / DHCP | Servicios: páginas editables, registros DNS, pool DHCP |
| CLI de Cisco IOS | CLI con las órdenes reales y abreviaturas (ver abajo) |
| VLAN, troncales 802.1Q | `vlan`, `switchport mode access/trunk`, `switchport access vlan`, `interface range` |
| Spanning tree | Simplificado: bloquea los enlaces redundantes entre switches |
| DHCP en el router | `ip dhcp pool`, `network`, `default-router`, `dns-server`, `ip dhcp excluded-address` |
| Rutas estáticas | `ip route` (y ruta por defecto 0.0.0.0 0.0.0.0) |
| Modo simulación, lista de eventos, detalle de capas | Pausa (F5), Paso (F6), velocidad, filtros por protocolo, clic en el sobre |
| Add Simple PDU | PDU simple, con lista de resultados Correcto / Fallido |
| Notas en el lienzo | Nota |

Además:

- **Calcular IPs**: reparte las direcciones de todo el esquema de una vez (IP fija o DHCP), con las rutas
  estáticas entre routers.
- **Comprobación de IP fija**: si a un equipo se le pone una IP a mano y el resto va por DHCP, avisa si
  no es de su red, si es la dirección de red o de broadcast, si ya la tiene otro equipo o si la puerta de
  enlace no encaja.
- **Impresora de red**: recibe los trabajos de `imprimir <ip> <texto>` y los muestra en «Trabajos impresos».
- **Calculadora IP** (Herramientas → Calculadora IP, Ctrl+I): red, broadcast, primera y última IP,
  número de equipos y la máscara en binario, con la cuenta de cada resultado. Trae una memoria justificativa
  en PDF pensada para alumnos de ESO, y también funciona sola en el navegador
  ([web/calculadora_ip.html](web/calculadora_ip.html)).
- **Imprimir y memoria en PDF** (Archivo): el esquema y toda la configuración en un documento para entregar.

Órdenes IOS admitidas (con abreviaturas, `?` para ayuda, `do` en modo configuración, Ctrl+Z):
`enable`, `disable`, `configure terminal`, `hostname`, `interface`, `interface range`,
`ip address`, `no ip address`, `shutdown`, `no shutdown`, `description`, `ip route`,
`ip dhcp pool`/`network`/`default-router`/`dns-server`, `ip dhcp excluded-address`,
`vlan`/`name`, `switchport mode access|trunk`, `switchport access vlan`, `ping`, `traceroute`,
`show ip interface brief`, `show ip route`, `show running-config`, `show arp`,
`show ip dhcp binding`, `show ip dhcp pool`, `show vlan [brief]`, `show mac address-table`,
`show interfaces trunk`, `show spanning-tree`, `clear arp-cache`, `clear mac address-table`,
`copy running-config startup-config`, `write`.

Todavía **no** incluye: enrutamiento dinámico (RIP, OSPF), NAT, listas de acceso,
router-on-a-stick (subinterfaces), Telnet/SSH, correo/FTP, tipos de cable
(directo/cruzado) ni la vista física.

## Modo Simulado y modo Real

Un selector en la barra superior cambia todo el programa:

- **Simulado**: todo ocurre dentro de SalariaNet, con las IP del esquema.
- **Real**: un PC del esquema (con la etiqueta **REAL**) representa a este ordenador. Toma su IP,
  máscara, puerta de enlace y DNS reales (en Windows los lee del sistema; en Linux, con `ip`). Su terminal
  ejecuta de verdad `ping`, `tracert`, `ipconfig`, `nslookup` y `arp -a`; su navegador abre páginas reales;
  y `mensaje <ip> <texto>` llega a otro ordenador que tenga SalariaNet abierto. Cuando se hace `ping` a un
  ordenador con SalariaNet, en ese ordenador aparece un aviso.
- Clic derecho en un PC → **Es este ordenador (modo real)** para elegir cuál es, o **Es otro ordenador
  del aula (modo real)** para que represente a otro: se elige de la lista de ordenadores con SalariaNet
  abierto o se escribe su IP a mano.

El programa nunca cambia la configuración del ordenador: `ipconfig /renew` y `/release` no se permiten en
modo Real. Al volver a Simulado se recupera la configuración del esquema, que es la que se guarda en el
archivo.

## Intranet del aula

Cada **Conexión aula** es un cable que llega hasta SalariaNet abierto en otro ordenador. Los programas de
la misma red **se descubren solos**, así que no hace falta escribir IPs:

1. **Profesor**: un switch y tantas Conexiones aula como alumnos, conectadas al switch. No se configuran:
   se quedan esperando.
2. **Alumno**: su PC conectado a una Conexión aula → doble clic → elige el ordenador del profesor en la
   lista → **Conectar**. Se usa sola una conexión libre del profesor, que se une al alumno
   automáticamente.
3. Si dos alumnos eligen la misma conexión, el segundo recibe el aviso de que está ocupada y elige otra.

El punto de la nube se pone verde cuando los dos ordenadores se ven, y la barra de estado dice cuántos
SalariaNet hay abiertos en el aula. Si la red del centro bloquea la difusión, queda la configuración manual
(IP y puerto del otro equipo) en la misma ventana.

SalariaNet usa los puertos **UDP 41000 a 41050** de la red local: el 41000 para descubrir los otros
ordenadores, los mensajes y los avisos de ping, y del 41001 al 41050 para las Conexiones aula.

## Documentación

- **Guía de uso**: [Guia_SalariaNet_actualizada.pdf](Guia_SalariaNet_actualizada.pdf). Dentro del
  programa, en Ayuda → Cómo se usa.
- **Memoria justificativa de la calculadora IP**:
  [docs/Memoria_calculadora_IP.pdf](docs/Memoria_calculadora_IP.pdf). Explica cómo se calculan la red, el
  broadcast y el número de equipos, con las fórmulas.

Las dos van también dentro de los instaladores: en la carpeta del `.zip` de Windows y en
`/usr/share/doc/salarianet` en Ubuntu.

## Para desarrolladores

```
red_aula.py           arranque del programa
redaula/
  motor.py            simulación: equipos, interfaces, paquetes y protocolos
  interfaz.py         ventana principal, lienzo y ventanas de cada equipo (PySide6)
  ios.py              línea de comandos al estilo Cisco IOS
  real.py             modo Real: configuración y órdenes del ordenador (Windows y Linux)
  autoip.py           Calcular IPs y comprobación de las IP fijas
  calculadora.py      calculadora IP
  memoria.py          impresión y memoria en PDF
recursos/             iconos y logotipo
docs/                 guía, memoria de la calculadora y capturas
web/                  calculadora IP en HTML5
pruebas/              pruebas automáticas
```

Cada prueba se ejecuta sola y guarda sus capturas en `pruebas/capturas`, por ejemplo:

```bash
python3 pruebas/prueba_escenarios.py
```

### Generar los instaladores

- **Windows**: `construir_exe.bat` (o `python construir_exe.py`) genera `dist/SalariaNet.zip` con
  PyInstaller.
- **Ubuntu**: `construir_deb.bat` en Windows, o `python3 construir_deb.py` en Linux, genera
  `dist/salarianet_<versión>_amd64.deb`. Descarga PySide6 6.6.3.1 para Linux (la última versión que
  funciona con el Python 3.8 de Ubuntu 20.04), así que no necesita herramientas de Debian.

Para publicar una versión, se crea una *release* en GitHub y se adjuntan los dos archivos de `dist/`.

## Licencia

SalariaNet © 2026 Alfonso José Martos Torres, I.E.S. Ivlia Salaria.

Este programa es software libre: puedes redistribuirlo y modificarlo según los términos de la
**Licencia Pública General de GNU** publicada por la Free Software Foundation, ya sea la **versión 3** de
la licencia o, a tu elección, **cualquier versión posterior**.

Se distribuye con la esperanza de que sea útil, pero **sin ninguna garantía**, ni siquiera la garantía
implícita de comerciabilidad o de idoneidad para un fin determinado. El texto completo de la licencia está
en [LICENSE](LICENSE).

Los instaladores incluyen PySide6 y Qt 6 sin modificar, que se distribuyen con la licencia LGPL v3.
