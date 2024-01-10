# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app_flask

# Copy the dependencies file to the working directory
COPY requirements.txt .

# Install any dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Instalo curl para poder hacer ping al keycloak
#RUN apt update
#RUN apt install curl

# Copy the content of the local src directory to the working directory
COPY . .

# Specify the command to run on container start
CMD [ "python", "./app.py" ]

# This dockerfile does not expose any ports. If your application listens on a port, 
# such as 3000, you should add the following line to your Dockerfile:
EXPOSE 3000
