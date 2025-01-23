# Configuración de Proxy Inverso

En este proyecto se han realizado 3 páginas que alojaremos en 3 contenedores dockers con su respectivo dockerfile.

## Requisitos
- Docker instalado en el sistema
- Conexión a internet para descargar imágenes de Docker
- Docker compose instalado en el sistema
- Apache para la configuración de proxy inverso

## Instrucciones de despliegue
1. Clona este repositorio en tu máquina:
   ```bash
   git clone [<URL_DEL_REPOSITORIO>](https://github.com/ddrafa8b/Proxy_Inverso.git)
   cd Proxy_Inverso
   ```

2. Construye las imagenes de los contenedores:
    ```bash
    sudo docker build -t auladaw .
    sudo docker build -t bicicleta .
    sudo docker build -t coches .
    ```
3. Inicia los contenedores con puertos distintos:
    ```bash
    sudo docker run -d -p 8080:80 –name cnt_auladaw auladaw
    sudo docker run -d -p 8081:80 –name cnt_bicicleta bicicleta
    sudo docker run -d -p 8082:80 –name cnt_coches coches
    ```

## Integración de Apache con Docker
    ```bash
    sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/     cocheses-selfsigned.key -out etc/ssl/certs/cocheses-selfsigned.crt
    ##########################################################################
    a2ensite www.aula2daw.com.conf
    a2ensite www.bicicletas.com.conf
    a2ensite www.coches.com.conf
    ```
    
Cambiar el archivo hosts por el de tu máquina o simplemente añadir las rutas al tuyo, al igual que con el archivo ports que deberás poner Listen 8084 (o uno que sepas que no dará conflicto) en lugar de la 8080.

4. Abre tu navegador y accede a las rutas que has conbfigurado en el paso anterior.

## Estructura del Proyecto
- `Dockerfile`: Configuración de los contenedores
- `ports.conf`: Los Listen de los puertos
- `hosts`: Para que al buscar nuestras páginas usemos rutas distinguidas
- `www.xxxx.es.conf`: Configuración de enrutamiento específica por cada página
- `aula2daw/` y demás: contenedores del DockerFile y del archivo html de la página específica.

##Autor
Rafael Díaz Delgado 2ºDAW
