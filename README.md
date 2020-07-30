# JENKINSFILES PROJECT

# Prerequisitos

- Configurar nodos con etiquetas "bash" y "bash2"
![](imgs/nodobash.gif)

- Para el error que se presenta al configurar el nodo con ssh, verificar que se encuentre la dirección del nombre de la maquina en el archivo known_hosts, de no ser así, agregarlos, una forma es conectarse directo vía ssh y nos saldra la opción de realizarlo. 

    Otra forma es mediante el comando 
    ```bash
    ssh-keyscan -H <HOSTNAME> >> ~/.ssh/known_hosts 
    ```
    Este comando agrega el **fingerprint** del host.

- Cuando el nodo sea configurado con private key, a parte de que debe estar en known_hosts debemos verificar que este en el archivo **authorized_keys** la parte publica de la llave.

- Script para ejecutar **jenkinsci/blueocean** en Mac
```bash 
#!/bin/bash
docker run -u root --network jenkins -v jenkins-docker-certs:/certs/client -v /Users/isortegah/Jenkins:/var/jenkins_home -v /Users/isortegah:/home -v /var/run/docker.sock:/var/run/docker.sock --group-add daemon -p 8082:8080 jenkinsci/blueocean
```
# Referencias

- [Host Key Verification for SSH Agents](https://support.cloudbees.com/hc/en-us/articles/115000073552-Host-Key-Verification-for-SSH-Agents)
- [Using Docker with Pipeline](https://www.jenkins.io/doc/book/pipeline/docker/#specifying-a-docker-label)