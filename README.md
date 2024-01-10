# Flask Keycloak OIDC Application 🌐

## Description
This project is a web application developed with Python's Flask, integrated with Keycloak for user authentication through the OpenID Connect (OIDC) protocol and the Authorization Code flow.
It serves as an example for user authentication in an application using an Identity Provider like Keycloak or Okta, in this case using a Keycloak server to manage user identities.

## Features 🔐
- **Secure Authentication**🔐: Uses Keycloak to authenticate users, offering a robust layer of security and session management.
- **User Management**👥: Allows user registration, login, and logout supported by Keycloak.
- **OIDC Integration**🔗: Implements the OIDC protocol for seamless integration and standard authentication flow.

## Requirements 📋
- Python3 🐍
- Flask 🌶️
- Keycloak 🗝️

## Installation and Configuration 🛠️

### Keycloak 🗝️

#### Set admin credentials as environment variables
```sh
vim ~/.bashrc
export KEYCLOAK_ADMIN='your_admin'
export KEYCLOAK_ADMIN_PASSWORD='your_password'
source ~/.bashrc
```

Creating a realm in Keycloak

- Realms -> Create realm
- Name it myorg

Registering the OIDC client

The OIDC client is the Flask application.

- Client_id: ``test_web_app``
- Enable Client Authentication
- Enable only Standard Flow

Replace ``<ip_flask>`` with your Flask server's IP:
In Login settings:

- Home URL: ``http://<ip_flask>:3000``
- Valid redirect URIs: ``http://<ip_flask>:3000/callback``
- Valid post logout redirect URIs: ``http://<ip_flask>:3000/loggedout``
- Web Origins: ``http://<ip_flask>:3000``

In Client -> Credentials copy the Client Secret to confApp in ``app.py``

### Flask 🌶️

To install dependencies:

- pip install -r requirements.txt

To deploy:

- python3 app.py
