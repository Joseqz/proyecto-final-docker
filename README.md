# Proyecto Final - Sistemas Operativos  
## Docker + Apache Proxy Inverso

Este proyecto implementa una arquitectura basada en contenedores Docker para desplegar una aplicación frontend desarrollada con **React** y **Vite**, accesible a través de un **servidor Apache** configurado como **proxy inverso**.  

## 📂 Estructura del proyecto

```
proyecto-final-docker/
│
├── 02-tictac-toe/              # Aplicación React con Vite
│   ├── Dockerfile
│   ├── package.json
│   └── src/...
│
├── apache-proxy-inverso/       # Configuración de Apache como proxy inverso
│   ├── Dockerfile
│   └── httpd.conf
│
├── docker-compose.yml          # Orquestación de contenedores
└── README.md                   # Documentación del proyecto
```

## ⚙️ Tecnologías utilizadas
- **Docker**: Contenerización de aplicaciones.
- **Docker Compose**: Orquestación multi-contenedor.
- **Apache HTTP Server**: Proxy inverso para redirección de tráfico.
- **Node.js + Vite + React**: Desarrollo frontend.
- **HTTP**: Comunicación entre contenedores.

## 🚀 Ejecución del proyecto

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/Joseqz/proyecto-final-docker.git
   cd proyecto-final-docker
   ```

2. **Levantar los contenedores**
   ```bash
   docker-compose up --build
   ```

3. **Acceder a la aplicación**
   - Abrir en el navegador: **http://localhost:8080**

## 📌 Descripción de contenedores

- **frontend** → Construye y sirve la aplicación React con Vite en el puerto `5173`.
- **apache-proxy** → Apache configurado como proxy inverso para redirigir peticiones al contenedor `frontend`.

## 🔧 Configuración de Apache (ejemplo en `httpd.conf`)

```apache
ServerName localhost

LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so

<VirtualHost *:80>
    ProxyPreserveHost On
    ProxyPass / http://backend:5173/
    ProxyPassReverse / http://backend:5173/

    ErrorLog /proc/self/fd/2
    CustomLog /proc/self/fd/1 combined
</VirtualHost>

```

## 📷 Vista previa
<img src="https://lh3.googleusercontent.com/pw/AP1GczMZSlsgtp7YzVQkioVV-6dZ5nxdM2WIw4ccGUv0ttPHvFp7tEr7qMMBEKzgiyZwKypUjFITTWcluixYvX3pjIbMrynS1K_qIggqxqWQD2_CtlE0lg=w2400">
Proyecto funcionando

## ✍️ Autor: CEDEÑO QUIROZ JEREMY JOSE
Proyecto desarrollado como trabajo final para la asignatura **Sistemas Operativos**.
