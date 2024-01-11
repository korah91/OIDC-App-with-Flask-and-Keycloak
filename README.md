# Flask Keycloak OIDC Application 🌐

## Open ID Connect (OIDC)

OpenID Connect (OIDC) protocol with Keycloak as the identity provider. OIDC is an authentication layer on top of OAuth 2.0, which allows clients to verify the identity of an end-user based on the authentication performed by an authorization server


## Description
This project is a web application developed with Python's Flask, integrated with Keycloak for user authentication through the OpenID Connect (OIDC) protocol and the Authorization Code flow.
It serves as an example for user authentication in an application using an Identity Provider like Keycloak or Okta, in this case using a Keycloak server to manage user identities.

After the user logs in, the ID token data is displayed on screen.

This project can be deployed using either two Virtual Machines or two containers with docker compose. The deployment using VMs involves more steps, such as creating a Realm in Keycloak and changing IP addresses within the code. On the other hand, docker compose simplifies the process by automatically setting up the Keycloak admin user and the Keycloak Realm to be used. However, docker compose only works on a Linux host OS due to the utillization of the host network type.

This type of network is used because, among other reasons, using the default docker compose network, the Flask app redirects the user to the Keycloak container when the user doesn't have access to it. I have tried many to solve this to no avail, so the Host network type is used.

## Features 🔐
- **Secure Authentication**🔐: Uses Keycloak to authenticate users, offering a robust layer of security and session management.
- **User Management**👥: Allows user registration, login, and logout supported by Keycloak.
- **OIDC Integration**🔗: Implements the OIDC protocol for seamless integration and standard authentication flow.

## Requirements 📋
- Python3 🐍
- Flask 🌶️
- Keycloak 🗝️

## Installation and Configuration in two machines (VMs) 🛠️

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

## Deployment with Docker Compose 🐳

Deploy both Flask and Keycloak containers using the following command

```docker compose up --build```

After the containers are running, you can verify the deployment by accesing 

- Flask WebApp: ```localhost:80```

- Keycloak server: ```localhost:8080```

### Shutting down

To stop and remove the containers, use the following command: 

```docker compose down```

## Demo
![alt text](https://github.com/korah91/Flask_Keycloak_Web_App/blob/main/images/demo_gif.gif "Demo")

