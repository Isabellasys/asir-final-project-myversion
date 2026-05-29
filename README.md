# HORSEBIT (My Version) 🐎

Proyecto Final de ASIR desarrollado para integrar administración de sistemas, redes, automatización y desarrollo web dentro de una misma infraestructura virtualizada.

El proyecto consiste en una simulación de carreras de caballos en tiempo real donde una interfaz web desarrollada por mí recibe información desde un backend en Python utilizando MQTT como sistema de mensajería y MariaDB para almacenar estadísticas de las carreras.

Toda la infraestructura fue desplegada y configurada en un entorno local virtualizado compuesto por 4 máquinas virtuales.

## 🌐 Demo de la interfaz

https://guileless-pegasus-cffa82.netlify.app

> La demo pública muestra únicamente la interfaz web. La infraestructura completa fue desplegada en un laboratorio local para el Proyecto Final de ASIR.

---

## Tecnologías utilizadas

* pfSense
* HAProxy
* Nginx
* Python
* MQTT (Mosquitto)
* MariaDB
* Ansible
* Bash
* HTML
* CSS
* JavaScript
* GitHub
* Netlify

---

## Arquitectura de la infraestructura

La infraestructura estaba formada por cuatro máquinas virtuales:

### VM 1 - pfSense

* Firewall principal.
* Gestión de red.
* Segmentación y control de tráfico.

### VM 2 - Nodo Central

* HAProxy para balanceo de carga.
* Mosquitto (MQTT).
* MariaDB.
* Backend principal en Python.
* Ejecución de playbooks Ansible.

### VM 3 - Servidor Web A

* Nginx.
* Despliegue de la aplicación web.

### VM 4 - Servidor Web B

* Nginx.
* Despliegue de la aplicación web.

```text
Clientes
    │
    ▼
 HAProxy
    │
 ┌──┴──┐
 ▼     ▼
Web A Web B

Nodo Central
├── Python
├── MQTT
└── MariaDB

pfSense
└── Firewall
```

---

## Automatización con Ansible

Utilicé Ansible para automatizar tareas de configuración y despliegue de los servidores.

Entre ellas:

* Instalación de paquetes.
* Configuración de servicios.
* Despliegue de la aplicación web.
* Gestión de permisos.
* Configuración de HAProxy.
* Automatización de tareas repetitivas.

---

## Comunicación en tiempo real

La simulación utiliza MQTT mediante Mosquitto para enviar la posición de los caballos en tiempo real.

La interfaz web recibe los mensajes y actualiza automáticamente la información mostrada al usuario sin necesidad de recargar la página.

---

## Base de datos

MariaDB almacena información relacionada con las carreras y estadísticas de los caballos.

La aplicación utiliza consultas SQL para registrar y actualizar resultados durante la simulación.

---

## Lo que he practicado con este proyecto

* Administración de sistemas Linux.
* Virtualización.
* Redes y firewalls.
* Balanceo de carga con HAProxy.
* Automatización con Ansible.
* Bases de datos MariaDB.
* Desarrollo web con HTML, CSS y JavaScript.
* Programación en Python.
* Comunicación mediante MQTT.
* Documentación y despliegue de proyectos.

---
## 🎥 Vídeo de demostración

Además de la demo online, grabé una pequeña demostración mostrando el funcionamiento de la aplicación desarrollada para el proyecto.

En el vídeo se puede ver:

* Inicio de una carrera.
* Actualización de la interfaz en tiempo real.
* Vista de escritorio.
* Vista móvil.

👉 https://youtu.be/L4A0ei0gYSA?si=wMjZ8katE8LHl6xG


## Autora

**Isabella**

Estudiante de Administración de Sistemas Informáticos en Red (ASIR).
