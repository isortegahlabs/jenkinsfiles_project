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

# Referencias

- [Host Key Verification for SSH Agents
](https://support.cloudbees.com/hc/en-us/articles/115000073552-Host-Key-Verification-for-SSH-Agents)