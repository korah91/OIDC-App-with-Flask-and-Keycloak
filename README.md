# Flask-Keycloak OIDC Application 🌐

## Descripción
Este proyecto es una aplicación web desarrollada con Flask de Python, integrada con Keycloak para la autenticación de usuarios mediante el protocolo OpenID Connect (OIDC) y el flujo Authorization Code. 
Sirve de ejemplo para autenticación de usuarios en una aplicación mediante un Identity Provider como Keycloak u Okta, en este caso utilizando un servidor Keycloak para gestionar las identidades de los usuarios.

## Características 🔐
- **Autenticación segura**🔐: Utiliza Keycloak para autenticar usuarios, ofreciendo una capa robusta de seguridad y gestión de sesiones.
- **Gestión de usuarios**👥: Permite el registro, inicio de sesión y cierre de sesión de usuarios con el soporte de Keycloak.
- **Integración OIDC**🔗: Implementa el protocolo OIDC para una integración transparente y un flujo de autenticación estándar.

## Requisitos 📋
- Python3 🐍
- Flask 🌶️
- Keycloak 🗝️

## Instalación y Configuración 🛠️


### Keycloak 🗝️

#### Establecer credenciales de administrador como variables de entorno
```sh
vim ~/.bashrc
export KEYCLOAK_ADMIN='tu_admin'
export KEYCLOAK_ADMIN_PASSWORD='tu_password'
source ~/.bashrc
```

#### Creación un realm en Keycloak

- Realms -> Create realm
- Llamarlo myorg

#### Registro del cliente OIDC

El cliente OIDC es la aplicación Flask.
- Client_id: ``test_web_app``
- Habilitar Client Authentication 
- Habilitar solo Standard Flow

Reemplazar ``<ip_flask>`` con la IP de tu servidor Flask:
En Login settings:
- Home URL: ``http://<ip_flask>:3000``
- Valid redirect URIs: ``http://<ip_flask>:3000/callback``
- Valid post logout redirect URIs: ``http://<ip_flask>:3000/loggedout``
- Web Origins: ``http://<ip_flask>:3000``

En Client -> Credentials copiar el Client Secret a confApp en ``app.py``


### Flask 🐍
Para instalar las dependencias:
- pip install -r requirements.txt

Para desplegar:
- python3 app.py