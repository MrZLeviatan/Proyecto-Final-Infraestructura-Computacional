<h1 align="center">

Proyecto Final Infraestructura Computacional

</h1>  

Diseñar y desplegar una solución de virtualización para consolidar la infraestructura tecnológica de una organización mediante el uso de contenedores. La solución debe aprovechar un nuevo servidor de mayor capacidad adquirido por la organización, optimizando el uso de recursos y garantizando la disponibilidad de servicios críticos.

## 📚 Tabla de Contenidos
1. [Contexto](#-contexto)
2. [Características](#-características)
3. [Herramientas](#️-herramientas)
4. [Configuración Inicial](#configuración-inicial)
5. [Configuración de RAID y LVM](#configuración-de-raid-y-lvm)
6. [Configuracion de Contenedores](#configuracion-de-contenedores)
   

---

## 📖 Contexto:
La organización dispone actualmente de tres servidores tipo torre que operan de manera aislada. Con la compra de un servidor más robusto, se busca migrar y centralizar sus servicios en esta nueva infraestructura. La solución propuesta deberá implementar contenedores para consolidar los servicios y mejorar la eficiencia operativa.

---

## 🌟 Características:

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

---

## 🛠️ Herramientas

  - ![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white)
    
  - ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)

  - ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)

--- 

## Configuración Inicial:

- Se actualiza el sistema:

  `ubuntu
    sudo apt update && sudo apt upgrade -y
  `    
       
- Instalar Docker:

  1. Instalar Docker:

     `ubuntu
       sudo apt install docker.io -y
     `
  2. Inicia el servicio de Docker, haciéndolo operativo:
     
     `ubuntu
       sudo systemctl start docker
     `
  3. Habilita el inicio automático de Docker en futuros reinicios del sistema.

      `ubuntu
       sudo systemctl enable docker
     `
  4. Verificacion Docker:

      `ubuntu
       sudo docker --version
     `
     
- Instalar Podman:
  
  1. Instalar Podman:

     `ubuntu
       sudo apt install podman -y
     `
  2. Inicia el servicio de Docker, haciéndolo operativo:
     
     `ubuntu
        podman --version
     `
---

## Configuración de RAID y LVM:

Se configuraron tres arreglos RAID nivel 1 utilizando discos disponibles, garantizando redundancia al duplicar los datos entre discos pareados. Posteriormente, se implementaron volúmenes lógicos con LVM sobre cada RAID, permitiendo una gestión flexible del espacio de almacenamiento. Los volúmenes fueron formateados y montados en directorios específicos para ser utilizados por los contenedores de Apache, MySQL y Nginx.

  -  Se verifica la crearion de 6 discos en la maquina virtual
    
      [![imagen-2024-11-22-075255627.png](https://i.postimg.cc/L8thZmJg/imagen-2024-11-22-075255627.png)](https://postimg.cc/hXGKkWbK)

  - Crear RAID Nivel 1:
     
     - Identificar discos disponibles:
       
       [![imagen-2024-11-22-083841563.png](https://i.postimg.cc/pTL1NVww/imagen-2024-11-22-083841563.png)](https://postimg.cc/DWRcLhy6)   

     - Crear RAID 1 mediante **mdadm**:

       [![3.png](https://i.postimg.cc/Mpdz1Hm4/3.png)](https://postimg.cc/4YHCgJMb)

    - Se Verifica la creacion de los 3 RAID:

      [![4.png](https://i.postimg.cc/MGHq5wsG/4.png)](https://postimg.cc/nXyyVyf8)


   - Crear Volúmenes Lógicos (LVM):

        - Crear volúmenes físicos:

          [![5.png](https://i.postimg.cc/J0q2SD0C/5.png)](https://postimg.cc/q6Nw3721)

        - Crear grupos de volúmenes:
          
          [![6.png](https://i.postimg.cc/sxNpBs0Z/6.png)](https://postimg.cc/QKcBwGDX)

       - Crear volúmenes lógicos:   

         [![7.png](https://i.postimg.cc/26phhCYs/7.png)](https://postimg.cc/94pDj5rb)

      - Montar los volumenes logicos en sus carpetas respetivas:

        [![8.png](https://i.postimg.cc/8cDFZcP0/8.png)](https://postimg.cc/CBPL1F8G)

---

## Configuracion de Contenedores

   - Crear Dockerfiles
     Un Dockerfile es un archivo de texto que contiene instrucciones secuenciales para construir una imagen de Docker personalizada. Este archivo permite automatizar la configuración de un entorno de ejecución, garantizando      consistencia y portabilidad para aplicaciones y servicios. La creación de un Dockerfile implica definir una base sólida y agregar capas de personalización según las necesidades específicas del proyecto.

     ### Crear dockerfile **Apache**
          
        - Creamos un archivo Dockerfile en el directorio apache :
    
          [![9.png](https://i.postimg.cc/DZNjsVv0/9.png)](https://postimg.cc/FdjV5BJX)
    
        -  Creamos un archivo .html ppara prueba:

           [![10.png](https://i.postimg.cc/0NXRtB5R/10.png)](https://postimg.cc/jWfF2vJZ)

      ### Crear dockerfile **MySql**

        - Creamos un archivo Dockerfile en el directorio mysql:
    
          [![11.png](https://i.postimg.cc/qR6Y1BZy/11.png)](https://postimg.cc/CBYm100x)

      ### Crear dockerfile **Nginx**

        - Creamos un archivo Dockerfile en el directorio nginx:

          [![12.png](https://i.postimg.cc/nLCwLcxg/12.png)](https://postimg.cc/HJ1tZmV9)
