# Herramientas propias del sistema

Linux incluye varias herramientas integradas que permiten monitorizar los recursos y el rendimiento del sistema. Estas herramientas suelen ser la primera línea de defensa para identificar problemas en tiempo real.

## Monitorización de procesos y recursos

### **top/htop**
- **Descripción:** Proporcionan una vista dinámica de los procesos activos y el uso de CPU y memoria.
- **Diferencia:** `htop` ofrece una interfaz más visual e interactiva que `top`.
- **Comandos:**
  - `top`: Inicia la herramienta.
  - `htop`: Inicia la versión interactiva.
- **Ejemplo:** Ejecutar `htop` para observar procesos en tiempo real.

### **vmstat**
- **Descripción:** Muestra estadísticas del sistema, incluyendo memoria, procesos, CPU y actividad del disco.
- **Comandos:**
  - `vmstat 5`: Actualiza las estadísticas cada 5 segundos.
  - `vmstat -s`: Proporciona un resumen de las estadísticas.

### **free**
- **Descripción:** Informa sobre el uso de memoria, incluyendo memoria libre, utilizada y swap.
- **Comandos:**
  - `free -h`: Muestra los valores en formato legible para humanos.

---

## Monitorización de discos

### **iostat**
- **Descripción:** Informa sobre la carga del sistema y el rendimiento de los discos.
- **Comandos:**
  - `iostat -x 5`: Detalles extendidos actualizados cada 5 segundos.
  - `iostat -d /dev/sda`: Monitoriza un disco específico.

### **df**
- **Descripción:** Muestra el espacio en disco disponible para los sistemas de archivos montados.
- **Comandos:**
  - `df -h`: Salida en formato legible para humanos.
  - `df -T`: Incluye el tipo de sistema de archivos.

### **du**
- **Descripción:** Informa sobre el uso de espacio de directorios o archivos.
- **Comandos:**
  - `du -sh /ruta/del/directorio`: Uso total de un directorio.
  - `du -ah /ruta`: Incluye archivos individuales en el análisis.

---

## Monitorización de redes

### **iftop**
- **Descripción:** Monitoriza el ancho de banda utilizado por las conexiones de red.
- **Comandos:**
  - `sudo iftop`: Inicia la herramienta.
  - `iftop -f "host 192.168.1.1"`: Filtra el tráfico por una IP específica.

### **iptraf-ng**
- **Descripción:** Proporciona estadísticas detalladas sobre el tráfico de red.
- **Comandos:**
  - `sudo iptraf-ng`: Accede al menú interactivo.

### **netstat/ss**
- **Descripción:** Muestra conexiones de red activas, tablas de enrutamiento y estadísticas de red.
- **Comandos:**
  - `ss -tuln`: Lista puertos abiertos y servicios en escucha.
  - `netstat -anp | grep :80`: Ver conexiones HTTP.

---

## Análisis de registros

### **journalctl**
- **Descripción:** Visualiza y analiza los registros del sistema (journal).
- **Comandos:**
  - `journalctl -xe`: Muestra eventos recientes con detalles extendidos.
  - `journalctl -u nginx`: Muestra registros específicos de un servicio.

### **dmesg**
- **Descripción:** Muestra mensajes del kernel, útil para depurar problemas de hardware.
- **Comandos:**
  - `dmesg | grep error`: Busca errores específicos.
