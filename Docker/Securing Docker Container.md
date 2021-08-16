# Securing Docker Container #
## 1. Don't run the container as the root user

By default many containers are configured to run as root. This is necessary to install packages and make configuration settings. Change the user to a non-root user after configuration is done.

## 2. Use a multi-stage build and a  "distroless" base image

If 


## 3. Harden the security of the host system
## 4. Use a container image scanner to detect vulnerabilities
## 5. Don't install/configure things within the Dockerfile without understanding the potential risks
