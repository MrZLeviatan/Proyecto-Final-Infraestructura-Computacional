<h1 align="center">

Proyecto Final Infraestructura Computacional

</h1>  

Diseñar y desplegar una solución de virtualización para consolidar la infraestructura tecnológica de una organización mediante el uso de contenedores. La solución debe aprovechar un nuevo servidor de mayor capacidad adquirido por la organización, optimizando el uso de recursos y garantizando la disponibilidad de servicios críticos.

## 📚 Table of Contents / Tabla de Contenidos
1. [Contexto](#contexto)
2. [Características](#características)

---

## Contexto:
La organización dispone actualmente de tres servidores tipo torre que operan de manera aislada. Con la compra de un servidor más robusto, se busca migrar y centralizar sus servicios en esta nueva infraestructura. La solución propuesta deberá implementar contenedores para consolidar los servicios y mejorar la eficiencia operativa.


## Características
- Virtualización:
  - Uso de contenedores para consolidar servicios en un único servidor físico.
  - Herramientas utilizadas: Docker y Podman para la creación y gestión de imágenes y contenedores.
  
- Servicios Esenciales en Contenedores:
  - Apache: Servidor web para alojar y entregar contenido estático y dinámico.
  - MySQL: Base de datos relacional para el manejo de datos de la organización.
  - Nginx: Proxy inverso y servidor web para optimizar el manejo de tráfico.

- Configuración de Almacenamiento:
  - RAID Nivel 1: Tres configuraciones RAID 1 para redundancia de datos.
  - LVM (Logical Volume Manager): Tres volúmenes lógicos creados a partir de los RAID.
  - Integración de los volúmenes lógicos como almacenamiento persistente en los contenedores.
