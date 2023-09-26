# Tarea trabajando con volumenes

1. **Descarga la imagen 'httpd' y comprueba que está en tu equipo**
    
    + Este apartado lo hacemos junto al [siguiente](#enlace1) apartado, asi que lo explico ahí 

<br>

2. **Crea un contenedor con el nombre 'dam_httpd'**

    + <a name="enlace1"></a>Para crear un contenedor primero tenemos que buscar las imagenes para poder descargarlas, esto lo miramos desde la pagina web de [docker](https://hub.docker.com/search?q=). Para crear el contenedor con la imagen httpd usaremos el siguiente comando:
        <a name="enlace2"></a>
        >`docker run -dit --name dam_httpd httpd:2.4`

        El parametro *--name* nos permite poner un nombre específico al contenedor.
    
    + El siguiente comando nos sirve para comprobar que tenemos la imagen de httpd:
        >`docker image ls -a`
    
        Este comando nos enseñará algo parecido a esto:
        
        |REPOSITORY|TAG|IMAGE ID|CREATED|SIZE|
        |------|------|------|------|------|
        |httpd|2.4|7860e7628717|2 weeks ago|168MB|

<br>

3. **Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?**

    + Para poder acceder desde el navegador solamente tendremos que poner nuestra ip en el navegador
    + Para ver nuestra ip simplemente tenemos que usar el comando 
        >`ip a`

4. **Utiliza bind mount para que el directorio del apache2 'htdocs' este montado en un directorio que tu elijas**

    + Para montar el htdocs en un directorio que elijas, primero tenemos que borrar el contenedor.
    + Seguido de esto usaremos el mismo comando que el apartado [2](#enlace2) añadiendo antes de la imagen la variable -v Directorio_a_Usar:Directorio_donde_estaba. Este seria un ejemplo:
        > `docker run -dit --name dam_httpd -p 8000:80 -v /home/dam2/Documentos/Repositorios/Volumenes/htdocs:/usr/local/apache2/htdocs httpd:2.4`
    + A parte de añadir lo del directorio tambien hemos realizado un mapeo de puertos añadiendo la variable -p puertoMaquina:PuertoContenedor

    + ¿Como sabemos que ha funcionado? Simplemente poniendo nuestra ip en el navegador : y puerto de la maquina, ejemplo:
        >localhost:8000
    
    <br>

5. **Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador**


6. **Crea un volumen para eset mismo fin**

7. **Crea un contenedor 'dam_web1' que use este volumen para el 'htdocs'**

8. **Utiliza Code para hacer un hola mundo en html**

9. **Crea otro contenedor 'dam_web2' con el mismo volumen y a otro puerto, por ejemplo 9080**

10. **Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador:**

    - http://localhost:9080
    - http://localhost:8000

11. **Tienen que salir la misma página web**