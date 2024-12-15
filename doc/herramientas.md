# Monitorización en Linux

En este documento, se explican varios comandos utilizados para monitorizar procesos, recursos del sistema y redes en Linux. Cada comando incluye su funcionalidad básica, opciones comunes y comparaciones cuando es relevante.

---

## Herramientas propias del sistema
Linux incluye varias herramientas integradas que permiten monitorizar los recursos y el rendimiento del sistema. Estas herramientas suelen ser la primera línea de defensa para identificar problemas en tiempo real.

---

## Comandos para Procesos

### `ps`
**Básico:** Muestra información sobre los procesos en ejecución.

- `ps a`: Lista todos los procesos asociados con terminales.
- `ps aux`: Muestra todos los procesos en el sistema junto con información detallada como el usuario, uso de CPU/memoria, y el estado del proceso.
- `ps -C <comando>`: Filtra y muestra los procesos que coincidan con el nombre del comando especificado.

### `ps -eo user,pid,%cpu,%mem,time --sort=-%cpu | head -n 6`
**Básico:** Lista los procesos mostrando usuario, PID, uso de CPU y memoria, y tiempo de ejecución. Ordena por uso de CPU y limita a los 6 procesos principales.

### Comparación de `ps`
- `ps aux` es ideal para un panorama general de los procesos.
- `ps -C` es útil para localizar procesos específicos.
- Usar `ps -eo` con opciones como `--sort` y `head` proporciona un enfoque más analítico para priorizar procesos según recursos utilizados.

---

## Comandos de Monitorización en Tiempo Real

### `top`
**Básico:** Muestra una vista dinámica de los procesos y el uso de recursos.

- `top -b -o %CPU -n 3 | head -n 17 > 10procesos.txt`: Ejecuta `top` en modo batch, ordena por CPU y guarda los primeros 10 procesos en un archivo.

### `htop`
**Básico:** Interfaz interactiva y visual para monitorizar procesos. Permite navegar, buscar y gestionar procesos con facilidad.

- **Diferencia entre `top` y `htop`:** `htop` ofrece una interfaz más visual e interactiva que facilita la gestión de procesos.

### `atop`
**Básico:** Monitoriza procesos y recursos del sistema, guardando información histórica en archivos para un análisis posterior.

Fichero de configuración: atop utiliza un archivo de configuración para personalizar el comportamiento de la herramienta, como definir qué métricas capturar y la frecuencia de registro.

- Ubicación del archivo de configuración: El archivo de configuración de atop suele encontrarse en `/etc/default/atop`.

- Al combinar `htop` y `atop`, se obtiene un balance entre visualización en tiempo real y almacenamiento de registros.

### `vmstat`
**Básico:** Muestra estadísticas del sistema, incluyendo memoria, procesos, CPU y actividad del disco.

- `vmstat 5`: Actualiza las estadísticas cada 5 segundos.
- `vmstat -s`: Proporciona un resumen de las estadísticas.

---

## Comandos para Memoria

### `free`
**Básico:** Muestra información sobre memoria RAM y swap.

- `free -h`: Muestra los datos en formato legible (GB, MB, etc.).
- `free -s 3`: Actualiza la información cada 3 segundos.

---

## Comandos para Almacenamiento

### `df`
**Básico:** Muestra el espacio disponible en los sistemas de archivos.

- `df -h`: Presenta la información en un formato legible para humanos.
- `df -T`: Incluye el tipo de sistema de archivos.

### `du`
**Básico:** Calcula el uso del espacio en disco.

- `du -h`: Muestra los resultados en formato legible.
- `du -hs`: Resume el uso total del espacio de una carpeta o archivo.
- `du -ah /ruta`: Incluye archivos individuales en el análisis.

---

## Comandos de I/O

### `iostat`
**Básico:** Muestra estadísticas de entrada/salida del sistema.

- `iostat -m`: Muestra los datos en MB.
- `iostat -mh`: Incluye encabezados legibles.
- `iostat -x`: Proporciona un desglose detallado por dispositivo.
- `iostat -sx`: Ordena por uso del dispositivo.
- `iostat -d /dev/sda`: Monitoriza un disco específico.

---

## Comandos para Redes

### `tcpdump`
**Básico:** Captura paquetes de red para análisis detallado.

- Ideal para depuración en profundidad de problemas de red.

### `tcptrack`
**Básico:** Monitoriza conexiones TCP activas y su estado en tiempo real.

- Más visual que `tcpdump`, pero menos detallado.

### `iftop`
**Básico:** Monitoriza el ancho de banda utilizado por las conexiones de red.

- `sudo iftop`: Inicia la herramienta.
- `iftop -f "host 192.168.1.1"`: Filtra el tráfico por una IP específica.

### `iptraf`
**Básico:** Interfaz interactiva para monitorizar tráfico de red por interfaces y conexiones.

### `bmon`
**Básico:** Proporciona una representación visual del ancho de banda utilizado en cada interfaz.

### `netstat/ss`
**Básico:** Muestra conexiones de red activas, tablas de enrutamiento y estadísticas de red.

- `ss -tuln`: Lista puertos abiertos y servicios en escucha.
- `netstat -anp | grep :80`: Ver conexiones HTTP.

### Comparación de Comandos de Redes
- **`tcpdump`**: Más poderoso para diagnósticos específicos.
- **`tcptrack`**: Muestra el estado de las conexiones TCP de forma simple.
- **`iptraf`**: Detallado para análisis a nivel de interfaz.
- **`bmon`**: Mejor para visualizar tendencias de ancho de banda.

---

## Análisis de Registros

### `journalctl`
**Básico:** Visualiza y analiza los registros del sistema (journal).

- `journalctl -xe`: Muestra eventos recientes con detalles extendidos.
- `journalctl -u nginx`: Muestra registros específicos de un servicio.

### `dmesg`
**Básico:** Muestra mensajes del kernel, útil para depurar problemas de hardware.

- `dmesg | grep error`: Busca errores específicos.

