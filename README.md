# 🧪 HORSEBIT (My Version) - Laboratorio Avanzado de Infraestructura, Automatización y Diseño Web

Este repositorio contiene mi **versión personal y sandbox de experimentación técnica** basado en el ecosistema HORSEBIT. Desarrollé este laboratorio de forma totalmente autónoma para profundizar en el desarrollo Full-Stack, arquitecturas de alta disponibilidad, mensajería orientada a eventos (IoT) e Infraestructura como Código (IaC).

El objetivo de este entorno local fue diseñar una infraestructura robusta que eliminara por completo la configuración manual de servidores, conectando una interfaz visual de usuario interactiva con un flujo reactivo y transaccional backend en tiempo real.

---

## 🎨 Desarrollo Frontend y Diseño Web (100% Propio)

La interfaz visual de la plataforma no es una plantilla; ha sido conceptualizada y programada desde cero por mí:
* **Diseño UI/UX:** Creación de una interfaz limpia, atractiva y tematizada para la simulación de carreras de caballos, optimizando la experiencia del usuario.
* **Frontend Reactivo (JavaScript):** Programación de la lógica del cliente para consumir de forma asíncrona el protocolo de mensajería, permitiendo que las animaciones de los carriles y los paneles de estadísticas se actualicen instantáneamente en el navegador sin necesidad de recargar la página.

---

## 🏗️ Arquitectura de la Infraestructura Local (Ecosistema de Red)

El sistema se despliega sobre un entorno de virtualización compuesto por **3 máquinas virtuales (VMs)** en una red local aislada y segura:

1. **Seguridad y Enrutamiento perimetral (pfSense):** Segmentación de red y políticas estrictas de firewall para aislar y proteger el tráfico de los servidores.
2. **Alta Disponibilidad (HAProxy):** Configurado como balanceador de carga en capa 7 (HTTP, puerto `80`) distribuyendo las peticiones entrantes de los clientes hacia los nodos mediante el algoritmo *Round-Robin*.
3. **Servidores Web y Cómputo (Nginx + Python Backend):** Servidores de producción encargados de ejecutar el motor lógico de simulación y servir la interfaz web.

---

## ⚙️ Automatización como Código (Ansible Playbooks)

Para garantizar que el entorno sea 100% reproducible y agnóstico a fallos manuales, sistematicé todo el aprovisionamiento mediante Ansible:

* **Módulo de Balanceo:** Automatización de la instalación de `haproxy` y reconfiguración dinámica del archivo `/etc/haproxy/haproxy.cfg` para inyectar los bloques de balanceo hacia los nodos internos (`hipodromo-a` y `hipodromo-b`).
* **Módulo de Despliegue Web:** Automatización de la limpieza de directorios de producción (`/var/www/html`), clonación automatizada de la rama principal del repositorio de la web, asignación de permisos al daemon del sistema (`www-data`) y apertura de puertos mediante políticas en el firewall local con `UFW`.

---

## 🧠 Motor de Simulación en Tiempo Real (MQTT + SQL)

El corazón de la aplicación simula un flujo transaccional controlado por un script asíncrono en Python (`director.py`):
* **Mensajería Reactiva (MQTT):** Uso del protocolo ligero IoT con el broker **Mosquitto** para publicar las posiciones de los caballos en tiempo real en el topic `carrera/caballos`. Esto alimenta directamente la interfaz web que diseñé.
* **Persistencia Transaccional (MariaDB):** Esquema relacional (`schema.sql`) que gestiona estadísticas globales (victorias/derrotas), previene duplicidades de registros con sentencias `ON DUPLICATE KEY UPDATE` y asegura accesos restringidos bajo el principio de mínimos privilegios (`GRANT PRIVILEGES`).
* **Orquestador Bash:** Automatización del ciclo de vida del arranque del software mediante un script unificado (`carrera.sh`) que valida el demonio de `mosquitto`, regenera la base de datos a un estado limpio e inicia el bucle lógico en Python.

---

## 📂 Estructura del Repositorio

* **`index/`**: Frontend desacoplado (HTML/CSS/JS) desarrollado íntegramente para la interfaz de la simulación.
* **`deployment/`**: Playbooks de Ansible, configuraciones de red y scripts de orquestación en Bash (`carrera.sh`).
* **`database/`**: Inicialización del esquema relacional y queries SQL en MariaDB.
* **`logic/`**: Backend en Python (`director.py`) encargado del procesamiento lógico y comunicación MQTT.

---

## 🌐 Despliegue y Demostración Visual

Dado que el clúster de servidores, las bases de datos y las reglas de Ansible se ejecutan estrictamente en mi entorno virtualizado local, se expone la interfaz de usuario de forma pública para pruebas rápidas y demostración:

* **🔗 Demo en Vivo de la Interfaz (Netlify):** [guileless-pegasus-cffa82.netlify.app](https://asir-final-project-myversion.netlify.app.netlify.app)

### 📺 Demostración del Ecosistema en Acción (Vídeo)

Haz clic en la imagen de abajo para ver la demostración completa en YouTube, donde se muestra el diseño de la web interactuando en tiempo real con el motor de Python, el broker MQTT y las consultas transaccionales de la base de datos:

[![Ver demostración en YouTube](https://img.youtube.com/vi/L4A0ei0gYSA/maxresdefault.jpg)](https://www.youtube.com/watch?v=L4A0ei0gYSA)

---

## 👤 Creadora
* **GitHub:** [@Isabellasys](https://github.com/Isabellasys)
* Proyecto autónomo de diseño frontend, arquitectura de sistemas y automatización de infraestructura.
